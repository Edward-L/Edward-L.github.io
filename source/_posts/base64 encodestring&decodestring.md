title: base64 encodestring&decodestring
categories: python
date: 2014-9-28 15:30:16
tags: [python,base64] 
---

昨天中软吉大的比赛结束后，和大神聊了聊，收获颇多。最重要的一点就是要好好的打好基础，我也觉得我必须要好的把python学学深了，他很多的模块我都不是很清楚。例如拿base64来说，python简单的三行代码可以完成，而自己却还这么麻烦的去找工具。所以初步打算在国庆期间要对python进行进一步的加强。

下面是三行base64加密：
```
import base64
       
test = raw_input ("input what do you want to encode : \n")
testa = base64.encodestring(test)
       
print testa
```
下面是三行base64解密：
```
import base64
   
test = raw_input("input what do you want to decode: \n")
testa = base64.decodestring(test)
   
print testa
```
