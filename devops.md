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
