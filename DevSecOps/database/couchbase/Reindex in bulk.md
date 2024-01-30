```
#!/bin/bash QUERY_HOST=http://localhost:8091 USERNAME=Administrator PASSWORD=wcladmin for i in "tiffany-connector" do /opt/couchbase/bin/cbq -e $QUERY_HOST -u $USERNAME -p $PASSWORD -s="$( \ echo "BUILD INDEX ON \`$i\` (\`$( \ /opt/couchbase/bin/cbq -e $QUERY_HOST -u $USERNAME -p $PASSWORD -q=true -s="SELECT name FROM system:indexes where keyspace_id = '$i' AND state = 'deferred'" | \ sed -n -e '/{/,$p' | \ jq -r '.results[].name' | \ sed ':a;/.*/{N;s/\n/\`,\`/;ba}')\`)")" # Wait for completion until [ `/opt/couchbase/bin/cbq -e $QUERY_HOST -u $USERNAME -p $PASSWORD -q=true -s="SELECT COUNT(*) as unbuilt FROM system:indexes WHERE keyspace_id = '$i' AND state <> 'online'" | sed -n -e '/{/,$p' | jq -r '.results[].unbuilt'` -eq 0 ]; do sleep 5 done done
```


  
34,072,324

![[Pasted image 20230515154850.png]]