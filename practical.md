## ipad上很多照片（上千张），如何无线方式传送到笔记本电脑？
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
## Github经常打不开，或者打开特别慢，怎么办？
- 何解：找到官网IP地址、域名IP地址、静态资源地址，然后配置本机hosts文件，刷新DNS缓存即可
```
1.获取github最新IP地址
  https://ipaddress.com/website/github.com
  https://fastly.net.ipaddress.com/github.global.ssl.fastly.net
  https://github.com.ipaddress.com/assets-cdn.github.com
2.修改hosts文件，添加ip和域名：
  C:\Windows\System32\drivers\etc中的hosts文件
3.刷新DNS缓存
  打开cmd窗口，执行ipconfig /flushdns命令
```
