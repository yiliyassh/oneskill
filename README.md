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
## 实用一点通
[详情](practical.md)
### ipad上很多照片（上千张），如何无线方式传送到笔记本电脑？
- 问题描述：
```
1.ipad未越狱，设备和系统都有点古老，懒得刷机折腾；
2.没有专用的苹果数据线（上百大洋，能省则省~_~）。
3.空间严重不足，总量16G，没有安装iTunes。
4.可以正常wifi无线联网。
5.照片和图片截屏，有上千张，需要备份到笔记本上。
6.ipad开启ES-wifi传输后，可以浏览下载照片，需要手工逐个点击，心累啊！
```
- 解决过程：
- ipad端操作：
```
1.ipad上安装“ES文件浏览器"，app store里完成。
2.把系统中照片，复制到ES文件浏览器（必须：没有越狱，系统照片无法访问）。
3.开启WiFi传输（默认可上传，第2步复制后可下载系统图片）。
```
- 笔记本端操作：
```
1.windows系统上安装wget（任意版本）。
源码编译安装：http://ftp.gnu.org/gnu/wget/wget-latest.tar.gz
exe文件下载：https://jaist.dl.sourceforge.net/project/gnuwin32/wget/1.11.4-1/wget-1.11.4-1-setup.exe
2.获取pad图片的下载地址，编辑批处理文件mypad.bat，格式如下：
wget -c http://192.168.0.100:5050/download?path=%%2Fphoto%%2FIMG_0001.PNG -O 0001.PNG
...
wget -c http://192.168.0.100:5050/download?path=%%2Fphoto%%2FIMG_9999.PNG -O 9999.PNG
说明：
浏览器访问图片原始地址：http://192.168.0.100:5050/download?path=%2Fphoto%2FIMG_0001.PNG
windows下“%”为系统默认符合，需要转义，用两个%代替一个%：%换为%%。
3.泡杯茶，执行mypad.bat。
4.收工，需要时间取决于图片大小，数量和WiFi速度。
```
- 太大，太多，太慢，不要怪我^_^。
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
标准启动模式：
python -m http.server 8000
后台启动模式：
nohup python -m http.server 8000 &
指定日志文件启动模式：
nohup python -m http.server 8000 >> test.log 2>&1 &
```
- python2启动web服务
```
标准启动模式：
python -m SimpleHTTPServer 8000
后台启动模式：
nohup python -m SimpleHTTPServer 8000 &
指定日志文件启动模式：
nohup python -m http.server 8000 >> test.log 2>&1 &
```
