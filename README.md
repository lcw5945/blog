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
cat //查看当前文件内容  
touch filename //新建文件
vim filename // 编辑当前文件，进入后按下 i  开始编辑, 退出 esc 键后，输入 :wq  退出保存  或者  :q 退出 ，  只读模式文件保存 :w!  然后:q
alias //设置别名 长久有效设置方式是编辑.bashrc文件
//root用户：/root/.bashrc
//cary用户：/home/cary/.bashrc
//vim .bashrc
// alias pulljsdev='git --git-dir=/home/work-develop/git/starway-js-web/.git --work-tree=/home/work-develop/git/starway-js-web pull origin dev'
```

` ln是linux中又一个非常重要命令，它的功能是为某一个文件在另外一个位置建立一个同不的链接，这个命令最常用的参数是-s，具体用法是：ln –s 源文件 目标文件。
　　当我们需要在不同的目录，用到相同的文件时，我们不需要在每一个需要的目录下都放一个必须相同的文件，我们只要在某个固定的目录，放上该文件，然后在 其它的目录下用ln命令链接（link）它就可以，不必重复的占用磁盘空间。例如：ln –s /bin/less /usr/local/bin/less
　　-s 是代号（symbolic）的意思。
　　这里有两点要注意：第一，ln命令会保持每一处链接文件的同步性，也就是说，不论你改动了哪一处，其它的文件都会发生相同的变化；第二，ln的链接又 软链接和硬链接两种，软链接就是ln –s ** **，它只会在你选定的位置上生成一个文件的镜像，不会占用磁盘空间，硬链接ln ** **，没有参数-s， 它会在你选定的位置上生成一个和源文件大小相同的文件，无论是软链接还是硬链接，文件都保持同步变化。
`

