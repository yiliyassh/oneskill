# oneskill
skill in a word 一点就通，大道至简！
***
## 一句话爬虫
[详情](crawler.md)
### 下载中文版统计年签 :+1::+1::+1:
- 2005~2021年
```
wget http://www.stats.gov.cn/tjsj/ndsj/2021/left.htm|xargs cat left.htm|grep href|grep html|awk -F "'" '{print " http://www.stats.gov.cn/tjsj/ndsj/2021/"$2}'|grep -E '.jpg|.htm'|xargs wget 
```
### 下载英文版统计年签 :+1::+1::+1:
- 2007~2021年
```
wget http://www.stats.gov.cn/tjsj/ndsj/2021/left_.htm|xargs cat left_.htm|grep href|grep html|awk -F "'" '{print " http://www.stats.gov.cn/tjsj/ndsj/2021/"$2}'|grep -E '.jpg|.htm'|xargs wget 
```
### 下载统计公报 :+1::+1::+1:
- 2013~2021年
```
wget http://www.stats.gov.cn/tjsj/tjgb/ndtjgb/index.html|xargs cat index.html |grep -E "t202|t201[4-9]"|grep "cont_tit"|awk -F '"' '{print "http://www.stats.gov.cn/"$2}'|xargs wget
```
### 中国互联网络发展状况统计报告
- 下载第39~48次《中国互联网络发展状况统计报告》
```
wget http://www.cnnic.net.cn/hlwfzyj/hlwxzbg/index.htm|cat index.htm |grep "次"|grep pdf|awk -F "</a>" '{print $1}'|awk -F "=" '{print " http://www.cnnic.net.cn/hlwfzyj/hlwxzbg "$3}'|sed 's/target//g'|sed 's/"_blank">//g'|awk -F "'" '{print $1$2}'|sed 's/ //g'|sed 's/hlwxzbg./hlwxzbg/g'|xargs wget -c  
```
***
## 办公一点通
[详情](oa.md)
### 删除文档空行的几种方法
### LibreOffice 7.3.0.3
- 1.删除空格，按下 Ctrl + h 键盘组合键，弹出“查找和替换”对话框，点开“其他选项”，选中“正则表达式”，  在“查找内容”中输入：[:space:]
- 2.续查找替换操作，在“查找内容”中输入：^$
- 3.点击“全部替换”，删除全部空行。
## 运维一点通
[详情](devops.md)
### Linux中正则匹配的妙用
- 大量数据分批删除（文件上万个+）
```
  ls *|xargs -n 100 rm -rf
```
### python快速启动web服务
- python3启动web服务
```
python -m http.server 8000
```
- python2启动web服务
```
python -m SimpleHTTPServer 8000
```

