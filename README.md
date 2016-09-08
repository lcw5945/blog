# blog
node text

## linux

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
cd ~ //进入root目录
cd / //进入根目录
cd .. //返回上级目录
pwd // 查看目录当前的路径
ll  //查看当前目录内容详细信息
ls //查看当前目录下文件和目录
mv oldfile|dir newfile|dir  //移动文件或目录  或者 重命名文件或目录
yum install sofename  // 安装软件 (lrzsz 上传到linux 软件)
rz  //上传文件到linux 需要安装lrzsz 软件
```
