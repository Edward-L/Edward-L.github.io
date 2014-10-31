title: pyhton版手机app控制mac电脑锁屏
categories: python
date: 2014-10-02 15:30:16
tags: [python,app控制电脑锁屏] 
---

每天和一群灰阔生活在一起是一件非常有趣和危险的一件事。一不小心出去忘记锁屏，那么谁知道你的电脑会发生什么事呢。一天，小雨就忘记了锁屏就直接回寝室了，走在路上才想起来，内心是十分的不安阿！所以我们就在想能不能做一个app远程控制电脑锁屏呢！

第二天lightless就写了一个windows版的锁屏[传送门][1]，我很想用阿，怎么办呢！果断自己动手阿！我向lightless要了一个app的接口（因为我不会java！），然后我就开始用python写pc端的脚本了！
```
import urllib2
import re
import time
import os

while True:
    response = urllib2.urlopen("http://lightless.cn/RemoteControl/GetCode.php?sec-code=Edward_L")
    html = response.read()
    #print html
    res = re.findall("\d",html)
    #print res
    time.sleep(5)
   
    if res[0] == "0":
        os.system("pmset sleepnow")
        break
```
大概说下实现的原理吧。
就是每隔5秒读取一次数据库，如果手机端发出锁屏指令，则在数据库中存入0；不发出则为1；
如此一来，我只要判断是否为0即可。
为了能够关掉shell后也能运行，在执行这个脚本时要注意这样执行。
```
nonup shutdown.py &
```
之后输入exit，再关闭shell，这样就能愉快的掉shell，并能在后台执行了！
 
谁有更好的想法欢迎交流阿！



[1]: http://drops.hduisa.cn/archives/lock-screen-via-your-phone.html