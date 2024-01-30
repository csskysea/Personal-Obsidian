# Grafana 
## Grafana dashboard settting

- set variable
![[Pasted image 20230526142404.png]]
## Miscellaneous

- 怎么在 `Grafana` 上override `panel`上的Lables 为某个字段值？

假定给定的labels 为{“Loc”=“PBI”, “Sensor”=“3”}

比如要 by `Loc` 的值只需要选中panel 然后在grafana 右侧边栏上 修改显示名称 为 ​​${__field.labels.Loc}​


## Reference

- https://blog.51cto.com/u_12227788/5502781
