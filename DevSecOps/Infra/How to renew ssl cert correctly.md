
## How to check cert info?

```
openssl x509 -noout -text -in omnisaas_tiffany_cn.cer
```

the command line above will output domain names info and cert expiration time etc.
```Certificate:
    Data:
        Version: 3 (0x2)
        Serial Number:
            0c:7f:94:1a:b1:85:43:9e:c6:60:5c:0a:7c:42:0f:6d
    Signature Algorithm: sha256WithRSAEncryption
        Issuer: C=US, O=DigiCert Inc, CN=DigiCert Secure Site CN CA G3
        Validity
            Not Before: Mar 27 00:00:00 2023 GMT
            Not After : Mar 26 23:59:59 2024 GMT
        Subject: C=US, ST=New York, L=New York, O=Tiffany & Co., CN=omnisaas.tiffany.cn
        Subject Public Key Info:
            Public Key Algorithm: rsaEncryption
                RSA Public-Key: (2048 bit)
                Modulus:
                    00:bb:6f:fb:dd:32:5f:20:4f:75:e1:c1:18:4b:56:
                    63:bc:4d:14:7f:e3:7a:d1:c7:a0:5e:33:29:6c:2d:
                    a9:cf:8c:7f:cb:4a:e0:37:c3:56:32:a4:37:08:07:
                    23:c7:d3:06:97:2f:c5:97:14:2d:39:aa:09:fa:5e:
                    d3:91:40:2d:24:1f:72:24:7f:7a:a9:ce:cf:8b:a5:
                    77:87:61:e9:aa:a9:e5:98:db:2f:58:28:fd:f4:c8:
                    73:e8:01:e7:de:05:25:ff:22:53:88:1d:d4:e6:ec:
                    94:46:22:9a:7e:bd:b2:1f:7a:8c:7b:06:3c:09:05:
                    e4:6c:aa:3c:7f:65:57:94:af:00:cd:3d:bd:b5:c2:
                    ee:d4:f7:e8:5a:8f:9f:d6:b6:12:2b:1d:87:fe:98:
                    13:a7:53:fd:1e:a2:7a:32:6e:14:c8:7b:b3:3b:95:
                    57:05:6a:04:19:0a:00:9f:78:1c:06:3c:40:7c:d1:
                    bc:06:57:83:3c:a3:97:a8:7f:0d:aa:05:c8:ca:db:
                    3b:64:be:77:92:55:31:32:ef:67:f1:b9:62:13:35:
                    53:9a:4b:2e:a7:61:93:b6:14:d6:85:8b:20:d9:04:
                    44:dc:2b:48:bb:45:1e:d7:ad:8c:b7:cb:f7:21:57:
                    e3:bc:70:d5:4b:f1:e8:ba:bd:07:ea:46:8d:eb:e5:
                    61:49
                Exponent: 65537 (0x10001)
        X509v3 extensions:
            X509v3 Authority Key Identifier:
                keyid:44:D9:C8:4A:33:8E:D3:52:8D:A7:92:94:61:1F:9A:C8:A5:B7:EC:CB

            X509v3 Subject Key Identifier:
                2C:B1:AB:F5:EB:E0:60:08:F8:2D:02:8C:66:B4:26:BE:30:3E:C0:EB
            X509v3 Subject Alternative Name:
                DNS:omnisaas.tiffany.cn, DNS:admin.omnisaas.tiffany.cn
            X509v3 Key Usage: critical
                Digital Signature, Key Encipherment
            X509v3 Extended Key Usage:
                TLS Web Server Authentication, TLS Web Client Authentication
            X509v3 CRL Distribution Points:

                Full Name:
                  URI:http://crl.digicert.cn/DigiCertSecureSiteCNCAG3.crl

            X509v3 Certificate Policies:
                Policy: 2.23.140.1.2.2
                  CPS: http://www.digicert.com/CPS

            Authority Information Access:
                OCSP - URI:http://ocsp.digicert.cn
                CA Issuers - URI:http://cacerts.digicert.cn/DigiCertSecureSiteCNCAG3.crt

            X509v3 Basic Constraints:
                CA:FALSE
            1.3.6.1.4.1.11129.2.4.2:
                ...l.j.w.v..?
...Q.a....4....).hB
..gLZ:t....#........H0F.!....g.Rv..+@.j[_7.{..G.....hB.pT..!...)..J...Y..J?....H....2...QY3...w.s....L.x. }G......Q^q.*.k..z.wr.....#........H0F.!...i3d`........Hq.)].R..;...{.H...!.....F!..}4.o.v..>..n.-...]?\..6!.v.H..k..G4..j...0..R..V.,.....9..s....#........G0E. t...._.FEt.G%.....".....'......*.!..eI.'.....e.
PE'..n8..V....7lE..
    Signature Algorithm: sha256WithRSAEncryption
         62:e5:a4:bf:d1:22:81:29:ab:09:49:34:14:3e:84:ec:58:42:
         75:95:5e:c6:c3:87:3e:3a:92:b0:c0:55:b3:89:47:8e:03:9a:
         d0:fb:85:08:8d:60:f6:1b:56:b5:af:08:cb:94:b1:ec:23:69:
         f2:7b:e9:b6:48:fe:04:38:30:b4:1d:06:44:f9:76:3e:9b:40:
         46:bb:f1:bc:9b:b4:cd:ac:f9:ba:f8:16:44:40:9c:b5:7a:64:
         03:80:d9:5f:58:7b:e4:c5:df:ea:69:db:30:72:f8:91:1f:03:
         b0:90:7a:e8:fb:4d:61:50:ff:17:96:75:88:2f:d9:95:77:1d:
         c7:99:66:ac:8a:08:f2:5d:11:6b:2f:ff:0f:c6:05:43:9b:8f:
         8e:0b:e4:ca:b2:b4:67:18:5f:ed:48:db:10:66:ae:a1:0d:c1:
         39:9f:3b:6d:d4:30:3f:e3:87:10:bd:30:18:a7:c1:48:d5:16:
         91:21:c1:4b:ae:d8:e5:4f:8f:e3:76:47:d2:12:a0:d7:b4:fa:
         98:07:56:76:d0:e6:29:b2:ef:9c:d7:13:d6:d0:d6:c3:32:17:
         2f:d4:bb:9b:1e:89:66:e1:a8:4f:85:63:b8:f1:ae:92:10:7a:
         6a:91:d4:dd:fd:03:0b:27:5f:8f:61:c0:6d:7c:2f:5c:e9:c7:
         d3:29:27:8a
```

## How to export cert & private key , verify cert and renew cert?

- export `PEM` format cert from `PFX` format cert(need to input `Import Password`)
```
openssl pkcs12 -in Tiffany.pfx -nodes -out server.pem

Enter Import Password:
```
- export private key file and `.cert` format cert file from `PEM` format cert
```
openssl rsa -in server.pem -out server.key

openssl x509 -in server.pem -out server.crt
```
- verify if matched between `private key` and `.cert`.(to compare the output if the same)
```
openssl x509 -noout -modulus -in server.crt | openssl md5

openssl rsa -noout -modulus -in server.key | openssl md5
```

- for public cloud, then you  need to login cloud console and upload cert and key file in slb section in console.



#ssl
#devsecops



