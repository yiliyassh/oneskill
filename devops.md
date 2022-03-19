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

## Linux中正则匹配的妙用
- 大量数据分批删除（文件上万个+）
```
  ls *|xargs -n 100 rm -rf
```

- 批量删除数据（每月保留1,10,20，末日）
- 1月
```
  rm -rf *2022010[2-9]*;rm -rf *202201[1-2][1-9]*;rm -rf *20220130*
```
- 2月
```
  rm -rf *2022020[2-9]*;rm -rf *2022021[1-9]*;rm -rf *2022022[1-7]*
```  
- 3~9月
```
  rm -rf *2022[0-1][3-9]0[2-9]*;rm -rf *2022[0-1][3-9][1-2][1-9]*;rm -rf *20220[1,3,5,7,8]30*;rm -rf *20221[0,2]30*
```
- 10~12月
```
  rm -rf *20221[0-2]0[2-9]*;rm -rf *20221[0-2][1-2][1-9]*
```

## Python中-m的典型用法
### 1.快速启动web服务
- python3启动web服务
```
python -m http.server 8000
```
- python2启动web服务
```
python -m SimpleHTTPServer 8000
```
### 2.本地启动html格式
```
python -m pydoc -p 9000
```
### 3.调试py文件
```
python -m pdb test.py
```
### 4.测试运行时间
```
python -m timeit "'-'.join(str(n) for n in range(100))"
python -m timeit "'-'.join([str(n) for n in range(100)])"
python -m timeit "'-'.join(map(str,range(100)))"
```
### 5.多Python版本的环境中，精确地控制三方库的安装位置
```
python -m pip list
python -m pip install xxx
```
- 参考材料
```
https://docs.python.org/3.7/using/cmdline.html#cmdoption-m
https://snarky.ca/why-you-should-use-python-m-pip
https://www.python.org/dev/peps/pep-0338/
```
