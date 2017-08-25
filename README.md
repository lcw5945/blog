# blog
node text

## linux

ssh远程登录

```js
ssh -p port name@ip  //默认port 22
~ -> ctrl+z  // 退出远程主机 返回上一个主机 先输入~  然后在输入 ctrl + z
jobs  查看后台运行的远程主机
fg %1 再回到远程主机
ssh-copy-id user@host 复制SSH密钥到目标主机，开启无密码SSH登录 如果还没有密钥，请使用ssh-keygen命令生成
ssh -N -L2001:localhost:80 somemachine 从某主机的80端口开启到本地主机2001端口的隧道

useradd -p passwd username   添加用户
su username
ssh-keygen -C "youname"
cd ~/.ssh
touch authorized_keys  客户端id_rsa.pub 黏贴上
chmod 644 authorized_keys
chmod 700 ../.ssh

```

>nodejs npm gulp webpack install

``` js 
tar  xf node-v5.10.1-linux-x64.tar.gz -C /home/programFiles/
```
重命名目录
```
cd /home/programFiles/
mv node-v5.10.1-linux-x64/ nodejs
```
设置全局
```
ln -s /home/programFiles/nodejs/bin/node /usr/local/bin/node
ln -s /home/programFiles/nodejs/bin/npm /usr/local/bin/npm
```

`注意：如果移动软件或者别的原因 造成bin目录下node或者npm一闪一闪，先删除全局，重新设置`

查看安装好的全局node 和npm

```
node -v
npm -v 
```

全局安装 webpack gulp

``` js
npm install webpack -g
npm install gulp -g 
```

设置全局

```
ln -s /home/programFiles/nodejs/bin/gulp /usr/local/bin/gulp
ln -s /home/programFiles/nodejs/bin/webpack /usr/local/bin/webpack 
```

其他命令

``` js 
rm -f|-rf file|dir  //移除文件或目录  -f 强制删除  -rf 强制删除递归子目录
find . -type f -cmin +10 -name '*.html' -exec rm {} \;  删除10分钟之内变动的 意.html 结尾的文件
find  .  -type f  -exec mv {}   /Data/sc \;  搜索当前目录文件复制移动到Data/sc下
cd ~ //进入root目录
cd / //进入根目录
cd .. //返回上级目录
cd - //返回之前的目录
pushd dirname //将目录dirname压入目录堆栈，并进入目录dirname
dirs -v  // 显示当前堆栈目录信息
pushed //在堆栈最上层2个目录切换
pushd +n //进入 dirs -v 显示索引值得目录
popd //删除堆栈目录最上层目录
pwd // 查看目录当前的路径
ll  //查看当前目录内容详细信息
ls //查看当前目录下文件和目录
mv oldfile|dir newfile|dir  //移动文件或目录  或者 重命名文件或目录
yum install sofename  // 安装软件 (lrzsz 上传到linux 软件)
rz  //上传文件到linux 需要安装lrzsz 软件
sz   sz filename //下载linux文件到 windows 下载位置在终端download里设置
cat //查看当前文件内容   
touch filename //新建文件
vim filename // 编辑当前文件，进入后按下 i  开始编辑, 退出 esc 键后，输入 :wq  退出保存  或者  :q 退出 ，  只读模式文件保存 :w!  然后:q
vi 闪退为保存文件会生成.name.swap 文件, 删除即可
alias //设置别名 长久有效设置方式是编辑.bashrc文件
//root用户：/root/.bashrc
//cary用户：/home/cary/.bashrc
//vim .bashrc
// alias pulljsdev='git --git-dir=/home/work-develop/git/starway-js-web/.git --work-tree=/home/work-develop/git/starway-js-web pull origin dev'
chmod +x filename.sh  // 加入可执行sh命令 以后运行脚本用这个方式  ./filename.sh  也可以直接运行 bin/sh filename.sh
chmod a+x filname.sh  // 所有用户组拥有可执行此文件权限
//+ 表示增加权限、- 表示取消权限、= 表示唯一设定权限
//r:只读,w:写,x执行

chown -R lichunwei.  目录 --设置用户拥有目录包括子目录 -R
chown -R :h5 git   更改目录拥有组 包括子目录
chmod -R 771 git   更改权限 用户和用户组 拥有读写执行权限 其他用户拥有执行权限

ssh-keygen -C "name" 生成sshkey
~/.ssh 下 authorized_keys 是ssh连接的认证文件
/etc/sysconfig/iptables  防火墙端口配置文件
/etc/ssh/sshd.config  ssh配置文件  
/etc/init.d  系统启动配置文件
echo $LANG  查看系统语言
/etc/sysconfig/i18n  系统语言配置文件
/etc/bashrc  对所有用户有效的
~/.bashrc  只对当前用户有效
/etc/rc.d/rc.local . //开机启动配置
cp  // 主要是用于在同一台电脑上，在不同的目录之间来回copy文件 
cp -r dir1 dir2     //dir1 复制到dir2 内
cp -r dir1/. dir2  //复制dir1 内的内容到dir2
scp //主要是在不同的Linux系统之间来回copy文件 
scp -P port file name@ip:dir 
uname -r  //查看系统版本
lsb_release -a //查看系统发行版本
ps -ef | grep name  //查看name 进程
netstat   -anp | grep  portno（例如：netstat –apn | grep 80）

* 环境变量
方法一：直接运行命令export PATH=$PATH:/usr/local/webserver/php/bin 和 export PATH=$PATH:/usr/local/webserver/mysql/bin

使用这种方法，只会对当前会话有效，也就是说每当登出或注销系统以后，PATH 设置就会失效，只是临时生效。

方法二：执行vi ~/.bash_profile修改文件中PATH一行，将/usr/local/webserver/php/bin 和 /usr/local/webserver/mysql/bin 加入到PATH=$PATH:$HOME/bin一行之后

这种方法只对当前登录用户生效

方法三：修改/etc/profile文件使其永久性生效，并对所有系统用户生效，在文件末尾加上如下两行代码
PATH=$PATH:/usr/local/webserver/php/bin:/usr/local/webserver/mysql/bin
export PATH

最后：执行 命令source /etc/profile或 执行点命令 ./profile使其修改生效，执行完可通过echo $PATH命令查看是否添加成功。

****Firewall*****
CentOS 6:

vi /etc/sysconfig/iptables
service iptables restart

1） 永久性生效，重启后不会复原

开启： chkconfig iptables on

关闭： chkconfig iptables off

2） 即时生效，重启后复原

开启： service iptables start

关闭： service iptables stop

CentOS 7:

iptables:
systemctl restart iptables

firewall:
systemctl start firewalld.service#启动firewall
systemctl stop firewalld.service#停止firewall
systemctl disable firewalld.service#禁止firewall开机启动

```

设置alise

进入root目录  `cd ~`
打开.bashrc   `vim .bashrc`

脚本中使用alise 

```
#!/bin/bash –login
shopt -s expand_aliases  //开启alise使用
pulljsdev
```
`cp && scp`

cp [options] source... directory 将一个档案拷贝至另一档案，或将数个档案拷贝至另一目录
* 复制文件： 
* 命令格式： 
scp local_file remote_username@remote_ip:remote_folder 
或者 
scp local_file remote_username@remote_ip:remote_file 
或者 
scp local_file remote_ip:remote_folder 
或者 
scp local_file remote_ip:remote_file 

第1,2个指定了用户名，命令执行后需要再输入密码，第1个仅指定了远程的目录，文件名字不变，第2个指定了文件名； 
第3,4个没有指定用户名，命令执行后需要输入用户名和密码，第3个仅指定了远程的目录，文件名字不变，第4个指定了文件名； 
* 例子： 
scp /home/space/music/1.mp3 root@www.cumt.edu.cn:/home/root/others/music 
scp /home/space/music/1.mp3 root@www.cumt.edu.cn:/home/root/others/music/001.mp3 
scp /home/space/music/1.mp3 www.cumt.edu.cn:/home/root/others/music 
scp /home/space/music/1.mp3 www.cumt.edu.cn:/home/root/others/music/001.mp3 

* 复制目录： 
* 命令格式： 
scp -r local_folder remote_username@remote_ip:remote_folder 
或者 
scp -r local_folder remote_ip:remote_folder 

第1个指定了用户名，命令执行后需要再输入密码； 
第2个没有指定用户名，命令执行后需要输入用户名和密码； 
* 例子： 
scp -r /home/space/music/ root@www.cumt.edu.cn:/home/root/others/ 
scp -r /home/space/music/ www.cumt.edu.cn:/home/root/others/ 


`ln`


 ln是linux中又一个非常重要命令，它的功能是为某一个文件在另外一个位置建立一个同不的链接，这个命令最常用的参数是-s，具体用法是：ln –s 源文件 目标文件。
　　当我们需要在不同的目录，用到相同的文件时，我们不需要在每一个需要的目录下都放一个必须相同的文件，我们只要在某个固定的目录，放上该文件，然后在 其它的目录下用ln命令链接（link）它就可以，不必重复的占用磁盘空间。例如：ln –s /bin/less /usr/local/bin/less
　　-s 是代号（symbolic）的意思。
　　这里有两点要注意：第一，ln命令会保持每一处链接文件的同步性，也就是说，不论你改动了哪一处，其它的文件都会发生相同的变化；第二，ln的链接又 软链接和硬链接两种，软链接就是ln –s ** **，它只会在你选定的位置上生成一个文件的镜像，不会占用磁盘空间，硬链接ln ** **，没有参数-s， 它会在你选定的位置上生成一个和源文件大小相同的文件，无论是软链接还是硬链接，文件都保持同步变化。

### Nginx 配置

* nginx.conf
```
worker_processes     8;
worker_cpu_affinity 00000001 00000010 00000100 00001000 00010000 00100000 01000000 10000000;

error_log  /data/log/nginx/error.log;

events {
    worker_connections  8024;
        }

http {
    include  mime.types;
    default_type application/octet-stream;
    fastcgi_intercept_errors on;
    charset utf-8;
    server_names_hash_bucket_size 128;
    client_header_buffer_size 4k;
    large_client_header_buffers 4 32k;
    client_max_body_size 300m;
    sendfile on;
    tcp_nopush  on;
    keepalive_timeout 60;
    tcp_nodelay on;
    client_body_buffer_size 512k;
    server_tokens off;

    proxy_headers_hash_max_size 51200;
    proxy_headers_hash_bucket_size 6400;
    proxy_set_header   Host             $host;
    proxy_set_header   X-Real-IP        $remote_addr;
    proxy_set_header   X-Forwarded-For  $proxy_add_x_forwarded_for;
    proxy_next_upstream error timeout invalid_header http_502 http_504;
    proxy_connect_timeout 300; #5
    proxy_read_timeout  120; #60
    proxy_send_timeout  10; #5
    proxy_buffer_size  16k;
    proxy_buffers   4 64k;
    proxy_busy_buffers_size 128k;
    proxy_temp_file_write_size 128k;

    map $uri  $newuri {
        ~^.*appVer\x22:\x22(?<androidver>.*).*$    $androidver;
    }

    gzip on;
    gzip_min_length 1k;
    gzip_buffers  4 16k;
    gzip_http_version 1.1;
    gzip_comp_level 2;
    #gzip_types  text/plain application/x-javascript text/css application/xml;
    gzip_types text/plain application/x-javascript text/css application/xml application/javascript  text/javascript application/x-httpd-php image/jpeg image/gif image/png;
    gzip_vary on;

#    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
#                      '$status $body_bytes_sent "$http_referer" '
#                      '"$http_user_agent" "$http_x_forwarded_for"';

#    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
#                  '$status $body_bytes_sent "$http_referer" '
#                  '"$http_user_agent" "$http_x_forwarded_for"';

    log_format json '{"@timestamp":"$time_iso8601",'
        '"host":"$server_addr",'
        '"clientip":"$remote_addr",'
        '"size":$body_bytes_sent,'
        '"responsetime":$request_time,'
        '"upstreamtime":"$upstream_response_time",'
        '"upstreamhost":"$upstream_addr",'
        '"http_host":"$host",'
        '"url":"$uri",'
        '"domain":"$host",'
        '"xff":"$http_x_forwarded_for",'
        '"referer":"$http_referer",'
        '"agent":"$http_user_agent",'
        '"status":"$status"}';
    access_log  /data/log/nginx/host.access.log  json;

    server {
        listen       80  default_server;
        server_name  _;
        return       444;
        access_log  on;
    }


    include /usr/local/app/nginx/conf/vhosts/*.conf;
}
```

* testerh5
```
server {
        listen       80;
        server_name  testerh5.hefantv.com;
        add_header Access-Control-Allow-Origin *;
        add_header Access-Control-Allow-Headers X-Requested-With;
        add_header Access-Control-Allow-Methods GET,POST,OPTIONS;

        index  index.html index.htm;
        root /data/web/nginx/testerh5;

        rewrite "^/hefantv/(.*)$" http://testerstatic.hefantv.com/hefantv/$1 break;
        #rewrite "^/club/outs/rougeshower/(.*)$" http://testerh5.hefantv.com/club/outs/rougeshower/index.html break;

        location =/ {
        index  index.html index.htm;
        root /data/web/nginx/testerh5;
        }

        location ~* ^/wap {
            index       index.html index.htm;
            root        /data/web/nginx/testerh5;
        }

        location ~* ^/club {
            index       index.html index.htm;
            root        /data/web/nginx/testerh5;
        }

       location  ^~ /club/outs/rougeshower  {
            try_files $uri $uri/ /club/outs/rougeshower/index.html;
       }

       location  ^~ /club/outs/fighter  {
            try_files $uri $uri/ /club/outs/fighter/index.html;
       }

       location @rs {
            rewrite ^/(.*)$ http://testerh5.hefantv.com/club/outs/rougeshower;  
       }

      

        location ~* .*\.(html|htm|gif|jpg|jpeg|bmp|png|ico|txt|js|css|woff|eot|svg|mp4|mp3|TTF)$ {
            index  index.html index.htm;
            root /data/web/nginx/testerh5;
#           expires      7d;
            }

        location ~ .*\.(json)$  {
            proxy_set_header  X-Real-IP  $remote_addr;
            proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-For $remote_addr;
            proxy_pass http://testerstatic.hefantv.com;

          }

        location ~* .*$ {
            proxy_set_header  X-Real-IP  $remote_addr;
            proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header X-Forwarded-For $remote_addr;
            proxy_pass http://testerapi.hefantv.com;

          }

        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }

    access_log  /data/log/nginx/testerh5.log json;

}
```

* proxy

```
server {
        listen       80 ;
        server_name  testapidoc.hefantv.com;
        location / {
                proxy_set_header  X-Real-IP  $remote_addr;
                proxy_set_header  X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header X-Forwarded-For $remote_addr;
                proxy_pass http://127.0.0.1:9013; 
        }
        access_log  /data/log/nginx/h5apidoc.log json;
}
```

``` js
    ./nginx -s reload  //修改配置文件重启
    ./sbin/nginx -t  //配置文件是否正确 
    ./sbin/nginx -t  -c ./conf/nginx.conf   //指定文件路径  -c
``` 

ERR_CONTENT_LENGTH_MISMATCH 错误
查看 /usr/local/app/nginx/logs/error.log  错误指向 /data/log/nginx/error.log 打开
```js
2017/04/25 15:27:07 [crit] 12710#0: *18611 open() "/usr/local/app/nginx/proxy//3/04/0000000043" failed (13: Permission denied) while reading upstream, client: 114.248.125.112, server: testhyrp.hefantv.com, request: "GET /img/index/bg.png HTTP/1.1", upstream: "http://127.0.0.1:9007/img/index/bg.png", host: "testhyrp.hefantv.com"
```
说明是Nginx 没有权限读取/usr/local/app/nginx/proxy 目录
ps ngxin进程
```js
root      1122  1120  0 Apr21 ?        00:00:00 svlogd -tt /var/log/gitlab/nginx
root      3271     1  0 Apr21 ?        00:00:00 nginx: master process /usr/local/app/nginx/sbin/nginx
nginx    12707  3271  0 14:21 ?        00:00:00 nginx: worker process          
nginx    12708  3271  0 14:21 ?        00:00:00 nginx: worker process          
nginx    12709  3271  0 14:21 ?        00:00:00 nginx: worker process          
nginx    12710  3271  0 14:21 ?        00:00:00 nginx: worker process          
nginx    12711  3271  0 14:21 ?        00:00:00 nginx: worker process          
nginx    12712  3271  0 14:21 ?        00:00:00 nginx: worker process          
nginx    12713  3271  0 14:21 ?        00:00:00 nginx: worker process          
nginx    12714  3271  0 14:21 ?        00:00:00 nginx: worker process 
```

master主进程是root 用户 其他是Nginx用户 所有要设置Nginx用目录权限

```
chown -R nginx /usr/local/app/nginx/proxy
```

```
location匹配命令

~      #波浪线表示执行一个正则匹配，区分大小写
~*    #表示执行一个正则匹配，不区分大小写
^~    #^~表示普通字符匹配，如果该选项匹配，只匹配该选项，不匹配别的选项，一般用来匹配目录
=      #进行普通字符精确匹配
@     #"@" 定义一个命名的 location，使用在内部定向时，例如 error_page, try_files
location ^~ ^/t/ {
     root /www/root/html/;  如果一个请求的URI是/t/a.html时，web服务器将会返回服务器上的/www/root/html/t/a.html的文件
}
location ^~ ^/t/ {
 alias /www/root/html/new_t/; 如果一个请求的URI是/t/a.html时，web服务器将会返回服务器上的/www/root/html/new_t/a.html的文件
}
```
#### vue router

```js
const router = new VueRouter({
        mode: 'history',
        base: '/outs/fighter/',
```	

nginx

```js 
location  ^~ /club/outs/fighter  {
            try_files $uri $uri/ /club/outs/fighter/index.html;
       }
```
	

### Mongodb 配置


``` js
配置开机启动-->  rc.d/rc.local 加入到开机配置
/usr/local/app/mongodb/bin/mongod --dbpath /usr/local/app/mongodb/data/mongodb/db --port 28017 --logpath /usr/local/app/mongodb/data/mongodb/log  --fork --auth 

进入数据
su root
cd /usr/local/app/mongodb/bin
./mongo --port 28017  //进入数据库 显示shell 版本 ⚠️看是否和db版本一致 db.version()

db.help() 
use admin  //使用admin db
show dbs
show collections
show users

db.createrUser //http://docs.mongoing.com/manual-zh/reference/method/db.createUser.html

{
	user : "admin",
 pwd: 'passwordk'
	roles : [
		{
			role : "userAdminAnyDatabase", //root , readWrite, read
			db : "admin"  //指定数据库
		}
	]
}

./mongod --dbpath /usr/local/app/mongodb/data/mongodb/db --port 28017 --logpath /usr/local/app/mongodb/data/mongodb/log --fork --auth  //设置后台运行，设置认证

db.auth('root', 'pwd') //mongo是关联的 要用root操作别的库的user 要 use admin -> auth root --> use tdb

mongodb://username:pwd@ip:port/dbname

新建数据库 并创建用户
1. use admin
2. db.auth('root', 'hefantv.123')  认证root
3. use apiDB    切换到apiDB数据库
4. db.testCON.insert({'name': '1'})  先在testCON 集合插入一条数据 apiDB才会生效
5. show dbs
6. db.createUser({"user" : "admin", "pwd" : "hefantv.123","roles" : [{"role" : "readWrite", "db" : "api"} ]}) 创建读写用户

导出数据库

./bin/mongoexport --port 28017 -d apidoc-dev -c databases -o /data/db/databases.json -u admin -p hefantv.123 
./bin/mongoexport --port 28017 -d apidoc-dev -c fields -o /data/db/fields.json -u admin -p hefantv.123
./bin/mongoexport --port 28017 -d apidoc-dev -c groups -o /data/db/groups.json -u admin -p hefantv.123
./bin/mongoexport --port 28017 -d apidoc-dev -c interfaces -o /data/db/interfaces.json -u admin -p hefantv.123
./bin/mongoexport --port 28017 -d apidoc-dev -c projects -o /data/db/projects.json -u admin -p hefantv.123
./bin/mongoexport --port 28017 -d apidoc-dev -c statecodes -o /data/db/statecodes.json -u admin -p hefantv.123
./bin/mongoexport --port 28017 -d apidoc-dev -c testenvs -o /data/db/testenvs.json -u admin -p hefantv.123
./bin/mongoexport --port 28017 -d apidoc-dev -c users -o /data/db/users.json -u admin -p hefantv.123

./bin/mongoimport --port 28017 -d apidoc-test -c databases /data/db/database.json -u admin -p hefantv.123 
./bin/mongoimport --port 28017 -d apidoc-test -c fields  /data/db/fields.json -u admin -p hefantv.123
./bin/mongoimport --port 28017 -d apidoc-test -c groups  /data/db/groups.json -u admin -p hefantv.123
./bin/mongoimport --port 28017 -d apidoc-test -c interfaces  /data/db/interfaces.json -u admin -p hefantv.123
./bin/mongoimport --port 28017 -d apidoc-test -c projects  /data/db/projects.json -u admin -p hefantv.123
./bin/mongoimport --port 28017 -d apidoc-test -c statecodes /data/db/statecodes.json -u admin -p hefantv.123
./bin/mongoimport --port 28017 -d apidoc-test -c testenvs  /data/db/testenvs.json -u admin -p hefantv.123
./bin/mongoimport --port 28017 -d apidoc-test -c users /data/db/users.json -u admin -p hefantv.123

```
### GitLab 配置

* 下载
https://www.gitlab.com.cn/installation/

```js
  /etc/gitlab/gitlab.rb gitlab 配置
  sudo gitlab-ctl reconfigure  重启
  gitlab-rake gitlab:backup:create 备份数据 生成到目录- /var/opt/gitlab/backups
  crontab -e   添加定时任务
  0 5 * * * /opt/gitlab/bin/gitlab-rake gitlab:backup:create  每天5点备份gitlab数据
  
  #数据恢复
  # 停止相关数据连接服务
  gitlab-ctl stop unicorn 
  gitlab-ctl stop sidekiq 

  # 从1393513186编号备份中恢复 
  gitlab-rake gitlab:backup:restore BACKUP=1466811825

  # 启动
  Gitlab sudo gitlab-ctl start
```

### Jenkins 配置

```
$ sudo vim /etc/sysconfig/jenkins
# 修改启动用户为root,默认为jenkins
JENKINS_USER="root"
# 修改运行端口为9999，默认为8080
JENKINS_PORT="9999"
```

启动Jenkins

```
service jenkins start 
```
如果报java错误 注意配置java环境变量，然后修改/etc/init.d/jenkins --> /usr/java/bin/java
```
# Search usable Java as /usr/bin/java might not point to minimal version required by Jenkins.
# see http://www.nabble.com/guinea-pigs-wanted-----Hudson-RPM-for-RedHat-Linux-td25673707.html
candidates="
/etc/alternatives/java
/usr/lib/jvm/java-1.8.0/bin/java
/usr/lib/jvm/jre-1.8.0/bin/java
/usr/lib/jvm/java-1.7.0/bin/java
/usr/lib/jvm/jre-1.7.0/bin/java
/usr/java/bin/java
```
```
/var/lib/jenkins/workspace  //项目工作空间
/var/lib/jenkins/user  // 用户目录
```

### nvm
windows nvm -->https://github.com/coreybutler/nvm-windows

淘宝镜像

```js

nvm node_mirror https://npm.taobao.org/mirrors/node/
nvm npm_mirror https://npm.taobao.org/mirrors/npm/



ps: C:\Users\Administrator\AppData\Roaming\nvm
```
