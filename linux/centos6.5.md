<h2>1、用ifconfig命令，显示结果只有lo，没有eth0</h2>
    解决
    
1. 输入ifconfig -a命令，可以看到eth0和lo。

2. 进入/etc/sysconfig/network-scripts目录，发现有ifcfg-eth0，即网卡（驱动）存在但未启用。
3. 输入ifconfig eth0 up，启用网卡。此时用ifconfig，只能看到inet6的地址，没有ip

4. vi /etc/sysconfig/network-scripts/ifcfg-eth0 文件， 把ONBOOT=no 改为 ONBOOT=yes，检查其他信息又没错误。

5. service network restart，重启

<h2>2、安装vsftpd</h2>
1.查看是否已安装过vsftpd &emsp;rpm -qa | grep vsftpd

2.如果未曾安装过则进行yum安装 &emsp; yum install vsftpd -y

3.vsftpd的主要命令：<br/>
&emsp;启动ftp命令#service vsftpd start<br/>
&emsp;停止ftp命令#service vsftpd stop<br/>
&emsp;重启ftp命令#service vsftpd restart<br/>

4.卸载vsftpd &emsp; rpm -e vsftpd

<h2>3、防火墙iptables</h2>
1.关闭防火墙&emsp;service iptables stop

2.禁止开机启动防火墙&emsp;chkconfig iptables off

3.查看防火墙状态&emsp;service iptables status

<h2>4、安装jdk</h2>
1.先下载jdk-8u191-linux-x64.tar.gz，用FlashFxp上传到Linux系统

2.解压jdk-8u191-linux-x64.tar.gz<br/>
tar  -zxvf  jdk-8u191-linux-x64.tar.gz

3.解压完成会看到jdk1.8.0_191的文件夹

4.创建/user/java目录，并将jdk1.8.0_191拷贝到/usr/java目录下<br/>
mkdir /usr/java<br/>
mv jdk1.8.0_191 /usr/java

5.修改环境变量
vi /etc/profile在文件最后添加<br/>
export JAVA_HOME=/usr/java/jdk1.8.0_191<br/>
export JRE_HOME=${JAVA_HOME}/jre<br/>
export CLASSPATH=.:${JAVA_HOME}/lib:${JRE_HOME}/lib:$CLASSPATH<br/>
export JAVA_PATH=${JAVA_HOME}/bin:${JRE_HOME}/bin<br/>
export PATH=$PATH:${JAVA_PATH}<br/>

6.用source /etc/profile 使刚添加的配置生效

7.测试是否安装成功<br/>
使用javac命令，不会出现command not found错误<br/>
使用java -version，出现版本为java version "1.8.0_191"

8.至此，安装成功！！！！

<h2>4、安装tomcat</h2>

1.下载压缩包apache-tomcat-7.0.92.tar.gz

2.用ftp上传到linux上

3.创建目录/usr/tomcat,解压tar -zxvf apache-tomcat-7.0.92.tar.gz

4.把解压后的文件夹apache-tomcat-7.0.92拷贝到/usr/tomcat目录下，进入apache-tomcat-7.0.92/bin,执行startup.sh

5.在浏览器访问192.168.75.134:8080<h4>能看到小猫,安装成功！</h4>

<h2>5、secrueCRT使用上传下载命令</h2>

1、服务器需要先安装 lrzsz     
    yum -y install lrzsz
    
2、上传命令rz

3、下载命令sz filename

4、修改上传和下载的默认磁盘位置:options — session options — X/Y/Zmodem


