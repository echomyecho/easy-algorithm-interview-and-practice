gsub(r,s)    在整个$0中用s替代r    
gsub(r,s,t)    在整个t中用s替代r    

```
awk -F "," '{str=gsub(/\t*| *$/,"",$3);ret=$1","$2","$3","NR;print ret}' 去除第三个字段的空格与制表符  
```  

awk -F "\t" '{if($3=="吉林") {gsub($3,"吉林省",$3);print $0}}'  area_province  
```  
220005 延边 吉林省
220007 松原 吉林省
220006 通化 吉林省
220003 白城 吉林省
220001 长春 吉林省
220002 四平 吉林省
220008 吉林 吉林省
220004 辽源 吉林省
220009 白山 吉林省
229999 吉林其它 吉林省
```  

对排好序的各个端数据取前1000  
```  
sort -t , -k3,3 -k4,4nr file | awk -F "," '{str=gsub(/\t*| *$/,"",$4);a[$3]++;{if(a[$3]<=1000) print $1","$2","$3","$4","a[$3]}}' z1 >zzz   
```
