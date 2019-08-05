# picoCTF2018_解题报告(部分)
*初学CTF，发现了picoCTF这个网站，我也是边学习边写了这篇文章，如果有疏漏的地方，还请多多谅解，享受寻找FLAG的乐趣吧。*
#### Forensics Warmup 1 - Points: 50 
只需要解压,并根据图片中的内容提交flag
![](http://upload-images.jianshu.io/upload_images/15974891-a5025c2322dda627.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> Flag:``` picoCTF{welcome_to_forensics} ```  

#### Forensics Warmup 2 - Points: 50
图片即为flag
![](http://upload-images.jianshu.io/upload_images/15974891-f5780c8cd7fa7488.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
> Flag:```picoCTF{extensions_are_a_lie}```  

#### General Warmup 1 - Points: 50
0x41表示16进制的41，查ASCII表可知为‘A’  
[ASCII 维基百科](https://zh.wikipedia.org/wiki/ASCII)
[ASCII 百度百科](https://baike.baidu.com/item/ASCII)  
> Flag:```picoCTF{A}```  

#### General Warmup 2 - Points: 50
进制转换：十进制的27转换为二进制：11011  
[CTF在线工具-ASCII与进制转换](http://ctf.ssleye.com/jinzhi.html)
或者直接用win自带的计算器也可以
> Flag:```picoCTF{11011}```  

#### General Warmup 3 - Points: 50
进制转换：16进制的3D转换为十进制：61  
> Flag:```picoCTF{61}```

#### Resources - Points: 50
点击链接在跳转的页面底端即可找到flag
也可以直接Ctrl+F直接搜索picoCTF字样
> Flag:```picoCTF{xiexie_ni_lai_zheli}```

#### Reversing Warmup 1 - Points: 50
由题可知，是一个ELF文件，跳转到该文件的目录下打开即可  
> Flag:```picoCTF{welc0m3_t0_r3VeRs1nG}```

#### Reversing Warmup 2 - Points: 50
将base64转换成ASCII码即可  
这里提供一个在线转换的网站：
[CTF在线工具-在线base64密码加解密](http://ctf.ssleye.com/base64.html)  
> Flag:```picoCTF{th4t_w4s_s1mpL3}```    

#### Crypto Warmup 1 - Points: 75
下载文件后，发现是一个密文和密钥的对应表，一一对应，即可找出明文
![](https://upload-images.jianshu.io/upload_images/15974891-3e52d906fc183a03.PNG?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)  
> Flag:```picoCTF{SECRETMESSAGE}```

#### Crypto Warmup 2 - Points: 75
根据题目可知，此密文是根据rot13加密而成的，查了一下这种加密规则：[ROT13](https://zh.wikipedia.org/wiki/ROT13)  
提供一个在线解密工具：[CTF在线工具-在线Rot13密码加解密](http://ctf.ssleye.com/rot13.html)    
对了这个解出来之后全是小写，记着把```ctf```变成大写  
> Flag:```picoCTF{this_is_crypto!}```

#### grep 1 - Points: 75
此题直接在shell中用grep命令即可，```grep pico *file```就是在```file```文件中查找```pico```字样
> Flag:```picoCTF{grep_and_you_will_find_c709fa94}```

#### net cat - Points: 75
[NetCat使用指南-简书](https://www.jianshu.com/p/cb26a0f6c622)
NC（netcat）被称为网络工具中的瑞士军刀，体积小巧，但功能强大。使用netcat工具连接到2018shell.picoctf.com at port 36356  
```
$ nc 2018shell.picoctf.com 36356
```
> Flag:```picoCTF{NEtcat_iS_a_NEcESSiTy_9454f3e0}```

#### HEEEEEEERE'S Johnny! - Points: 100
John the Ripper免费的开源软件，是一个快速的密码破解工具，用于在已知密文的情况下尝试破解出明文的破解密码软件，在Linux下使用以下命令即可解出账号密码
[Kali Linux：使用John the Ripper破解密码](http://topspeedsnail.com/John-the-Ripper-learn/)
```
$ john shadow
$ nc 2018shell3.picoctf.com 42165
Username: root
Password: hellokitty 
```
> Flag:```picoCTF{J0hn_1$_R1pp3d_5f9a67aa}```

#### strings - Points: 100
[strings命令-Linux命令大全](http://man.linuxde.net/strings)
此题使用```strings filename|grep "keyword"```即可  
> Flag:```picoCTF{sTrIngS_sAVeS_Time_d7c8de6c}```

#### pipe - Points: 110
此题是nc后使用一下grep即可。  
```
~$ nc 2018shell.picoctf.com 48696|grep "picoCTF"                                                    
```
> Flag:```picoCTF{almost_like_mario_f617d1d7}```

#### Inspect Me - Points: 125
此题我原本以为打开源代码就能找到FLAG了，后来发现只有1/3，最后乱闯乱转，发现两个自己写的```css```和```js```文件，点进去之后就可以看到另外那2/3的FLAG  
```<head>  
    <title>My First Website :)</title>
    <link href="https://fonts.googleapis.com/css?family=Open+Sans|Roboto" rel="stylesheet">
    <link rel="stylesheet" type="text/css" href="mycss.css">
    <script type="application/javascript" src="myjs.js"></script>
  </head>
``` 
> Flag:```picoCTF{ur_4_real_1nspect0r_g4dget_402b0bd3}```

#### grep 2 - Points: 125
此题依然是考验对于```grep```用法的掌握
```
$ grep "picoCTF" . -r -n
./files7/file25:2:picoCTF{grep_r_and_you_will_find_24c911ab}
``` 
> Flag ```picoCTF{grep_r_and_you_will_find_24c911ab}```

#### Aca-Shell-A - Points: 150
此题主要考察对于Linux命令的使用
```$ nc 2018shell.picoctf.com 42334 ```  
首先nc到这个地址：2018shell.picoctf.com 42334  
```tex
Sweet! We have gotten access into the system but we aren't root.
It's some sort of restricted shell! I can't see what you are typing
but I can see your output. I'll be here to help you along.
If you need help, type "echo 'Help Me!'" and I'll see what I can do
There is not much time left!
```
似乎需要我们echo  
```$ echo 'Help Me!'```  
```tex
You got this! Have you looked for any  directories?
```  
按照提示需要我们看一看目录下有什么  
```$ ls```  
```tex
blackmail                                                                                                                  
executables                                                                                                                
passwords                                                                                                                  
photos                                                                                                                     
secret
```  
secret目录很吸引人  
```$ cd secret```    
```  tex
Now we are cookin'! Take a look around there and tell me what you find!
```    
那我们就看看目录下有什么文件  
```$ ls```  
```Sabatoge them! Get rid of all their intel files!```  
要求我们删掉所有intel文件  
```$ rm intel*```  
```tex
Nice! Once they are all gone, I think I can drop you a file of an exploit!
Just type "echo 'Drop it in!' " and we can give it a whirl!
```
```$ echo 'Drop it in!'```
```tex
Drop it in!                                                                                                                
I placed a file in the executables folder as it looks like the only place we can execute from!
Run the script I wrote to have a little more impact on the system!
```
我们返回上一级目录，然后进入executables目录下，发现只有一个文件，我们打开它，发现开始输出很多16进制信息（我就不贴出来了），在最后一行发现了我们要的东西。  
```$ cd ..```  
```$ cd executables```  
```$ ./dontLookHere```
``` tex                                                                                
Looking through the text above, I think I have found the password. I am just having trouble with a username.
Oh drats! They are onto us! We could get kicked out soon!
Quick! Print the username to the screen so we can close are backdoor and log into the account directly!
You have to find another way other than echo!
```
要求我们打印出用户名，但是不能用echo，这就很奇怪了  
[Linux用户和权限管理-掘金](https://juejin.im/post/5b1e69dcf265da6e0d7a347e)
搜索了一下，在这篇文章中发现了
> whoami：显示当前用户的名称  

```$ whoami```  
```tex
l33th4x0r                                                                                                                  
Perfect! One second!
Okay, I think I have got what we are looking for. I just need to to copy the file to a place we can read.
Try copying the file called TopSecret in tmp directory into the passwords folder.
```  
按照要求复制tmp文件夹下的TopSecret文件到passwords的目录下  
```$ cp /tmp/TopSecret ../passwords```  
```tex
Server shutdown in 10 seconds...                                                                                           
Quick! go read the file before we lose our connection!
```  
有时间限制了，看来要抓紧了，打开TopSecret文件即可找到FLAG
```$ cd ..```
```$ cd passwords```
```$ cat TopSecret```
```tex
Major General John M. Schofield's graduation address to the graduating class of 1879 at West Point is as follows: The disci
pline which makes the soldiers of a free country reliable in battle is not to be gained by harsh or tyrannical treatment.On
 the contrary, such treatment is far more likely to destroy than to make an army.It is possible to impart instruction and g
ive commands in such a manner and such a tone of voice as to inspire in the soldier no feeling butan intense desire to obey
, while the opposite manner and tone of voice cannot fail to excite strong resentment and a desire to disobey.The one mode 
or other of dealing with subordinates springs from a corresponding spirit in the breast of the commander.He who feels the r
espect which is due to others, cannot fail to inspire in them respect for himself, while he who feels,and hence manifests d
isrespect towards others, especially his subordinates, cannot fail to inspire hatred against himself.                      
picoCTF{CrUsHeD_It_d6f202f1}                                                                                               
```
> Flag ```picoCTF{CrUsHeD_It_d6f202f1}```  
        
#### Client Side is Still Bad - Points: 150
乍一看是一个登录页面，随便输入了一串数字，发现提示错误，于是我们打开源代码，发现了如下的片段
```
  function verify() {
    checkpass = document.getElementById("pass").value;
    split = 4;
    if (checkpass.substring(split*7, split*8) == '}') {
      if (checkpass.substring(split*6, split*7) == 'ebbd') {
        if (checkpass.substring(split*5, split*6) == 'd_d0') {
         if (checkpass.substring(split*4, split*5) == 's_ba') {
          if (checkpass.substring(split*3, split*4) == 'nt_i') {
            if (checkpass.substring(split*2, split*3) == 'clie') {
              if (checkpass.substring(split, split*2) == 'CTF{') {
                if (checkpass.substring(0,split) == 'pico') {
                  alert("You got the flag!")
                  }
                }
              }
      
            }
          }
        }
      }
    }
    else {
      alert("Incorrect password");
    }
  }
```       
在if的条件中，就可以看到FLAG了
> Flag```picoCTF{client_is_bad_d0ebbd}```  
                       
#### Desrouleaux - Points: 150 
```
You'll need to consult the file `incidents.json` to answer the following questions.                                        
                                                                                                                                                                                                                                                    
What is the most common source IP address? If there is more than one IP address that is the most common, you may give any o
f the most common ones. 
```   
要求我们找出出现次数最多的source IP address
打开json文件后，"src_ip"中```45.238.158.24```出现了4次
```tex                                                                                                   
45.238.158.24                                                                                                              
Correct!                                                                                                                   
                                                                                                                                                                                                                                                     
How many unique destination IP addresses were targeted by the source IP address 45.238.158.24?
```     
问src_ip为45.238.158.24且dst_ip不重复的ticket出现了几次   
```tex                        
3                                                                                                                          
Correct!                                                                                                                   
                                                                                                                                                                                                                                                     
What is the number of unique destination ips a file is sent, on average? Needs to be correct to 2 decimal places.
```   
这个似乎有些麻烦，但我不会写python，且数据不多，所以手动统计了一下，顺便也提供一下从[picoCTF-2018 解题报告-闲言语](https://findneo.github.io/180929-picoctf/)找来的python脚本
```python
import json
j=json.load(open('incidents.json'))
tickets=j['tickets']
hashes=dict()
for t in tickets:
	if t['file_hash'] not in hashes.keys():
		hashes[t['file_hash']]=[t['dst_ip']]
	else:
		hashes[t['file_hash']].append(t['dst_ip'])
print (hashes)

```
然后算一下平均数即可
```tex          
1.25                                                                                                                       
Correct!                                                                                                                   
                                                                                                                                                                                                                                                  
Great job. You've earned the flag: picoCTF{J4y_s0n_d3rUUUULo_c74e3495} 
```
> Flag:```picoCTF{J4y_s0n_d3rUUUULo_c74e3495} ```

#### Logon - Points: 150
当我浏览网页时，发现输入任何非```admin```的用户名和密码都可以成功登录，但是网站只显示
```tex
Success: You logged in! Not sure you'll be able to see the flag though.
No flag for you
```
按照提示，我又使用```admin```的用户名登录，始终显示
```tex
I'm sorry the admin password is super secure. You're not getting in that way.
```
重新用非```admin```账号登录成功后，当我使用```EditThisCookie```时，发现了一个bug，```admin```的值是```False```，遂改为```True```，即可找到FLAG
> Flag: ```picoCTF{l0g1ns_ar3nt_r34l_a280e12c}```  

#### Reading Between the Eyes - Points: 150  
这题的信息隐藏在 RGB 三个通道的最低位中，借助 Stegsolve-->Analyse-->Data Extract 可以指定通道进行提取。[Stegsolve.jar](http://www.caesum.com/handbook/Stegsolve.jar)
也可以通过在线网站解决：[Steganography Online](http://stylesuxx.github.io/steganography/)
> Flag```picoCTF{r34d1ng_b37w33n_7h3_by73s}```

#### Recovering From the Snap - Points: 150
收到一个.dd结尾的文件，我们猜想有可能需要分离，用binwalk查看发现有多个文件，用foremost分离后得到8张照片，00005861.jpg即为FLAG
```binwalk animals.dd ```
```
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
39424         0x9A00          JPEG image data, JFIF standard 1.01
39454         0x9A1E          TIFF image data, big-endian, offset of first image directory: 8
672256        0xA4200         JPEG image data, JFIF standard 1.01
1165824       0x11CA00        JPEG image data, JFIF standard 1.01
1556992       0x17C200        JPEG image data, JFIF standard 1.01
1812992       0x1BAA00        JPEG image data, JFIF standard 1.01
1813022       0x1BAA1E        TIFF image data, big-endian, offset of first image directory: 8
2136576       0x209A00        JPEG image data, JFIF standard 1.01
2136606       0x209A1E        TIFF image data, big-endian, offset of first image directory: 8
2607616       0x27CA00        JPEG image data, JFIF standard 1.01
2607646       0x27CA1E        TIFF image data, big-endian, offset of first image directory: 8
3000832       0x2DCA00        JPEG image data, JFIF standard 1.01
3000862       0x2DCA1E        TIFF image data, big-endian, offset of first image directory: 8

```
```foremost animal.dd```
> Flag:```picoCTF{th3_5n4p_happ3n3d}```

#### admin panel - Points: 150
此题是一道流量分析，题目中有关于登录的提示
首先可以用```strings data.pacp|grep picoCTF```  
可以直接查到以下的内容  
```user=admin&password=picoCTF{n0ts3cur3_13597b43}```
也可以使用WireShark，在```tcp.stream 5```可以看到```password username```
```
POST /login HTTP/1.1
Host: 192.168.3.128
User-Agent: Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:59.0) Gecko/20100101 Firefox/59.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: http://192.168.3.128/
Content-Type: application/x-www-form-urlencoded
Content-Length: 53
Connection: keep-alive
Upgrade-Insecure-Requests: 1

user=admin&password=picoCTF{n0ts3cur3_13597b43}
```
