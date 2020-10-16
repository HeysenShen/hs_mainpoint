<h2>find命令</h2>

1.当前目录下查找文件名含abc的文件<br/>
find ./ -name abc

2.查找当前目录下内容含abc的所有文件<br/>
grep -rn "abc" ./

<h2>wc命令</h2>

1.查看指定文本有多少行<br/>
wc -l filename

2.查看文件里有多少个word<br/>
wc -w filename

3.文件里最长的那一行是多少个字<br/>
wc -L filename

<h2>查看每个目录大小</h2>
du -h --max-depth=1

<h2>查看目录下有多少个文件</h2>
ls -l |grep "^-"|wc -l

<h2>查看磁盘空间大小</h2>
df -h

<h2>按文件大小排序</h2>
ll -Srh

<h2>tar命令</h2>

tar -zcvf 压缩包名  被压缩的目录/文件   【打包】

tar -tf 压缩包名    【展示压缩包内容】

<h2>md5num</h2>
value=`md5sum "文件名或字符串"`

<h2>alias别名</h2>

设置临时别名    alias cd1='cd /home/admin/test'

删除临时别名    alias cd1

<h2>scp 命令</h2>

1、从本地复制到远程服务器

scp -r 当前目录 远程服务器用户名@远程ip:远程服务器目录
    
如: scp -r /test root@192.168.0.1:/domains/test