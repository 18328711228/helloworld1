#linux1.1
#1.以容易理解的格式列出/home 目录中所有以”d”开头的文件目录的大小
Ls -alh /home|grep^d


#2.列出/home 目录中所有以”s”开头的目录。
Ls -al /home|grep^s


#3.删除后缀名为.log 的所有，删除前逐一询问
rm -i *.log
#4.cp 命令 —n 和 -u的区别
--n是有重复文件不复制，
     -u 或 --update      使用这项参数之后，只会在源文件的修改时间(Modification Time)较目的文件更新时，或是名称相互对应的目的文件并不存在，才复制文件


#5.找你的用户目录下面的所有py文件,ls -l 查看他们的属性,然后把这些结果输入到一个文件之中
Find ~ -name “py”
Ls-l > /desktop/test1

#6使用ls查看根目录 并且每行显示3个信息
Ls / cd /


#7查看所有进程信息,只查看前3行
Ps -A|head -3



#8分析以下问题,并给出解决方案
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which could be identified for example by the help of the 'fuser' command.

查看该分区的使用者
sudo fuser -m /dev/sdb4
根据提示：
可以看出分区已自动挂载到/media/guest-mjsfmu/Windows目录下了，查看硬盘内容
sudo ls /media/guest-mjsfmu/Windows
确认看到了移动硬盘里的内容，包括要拷贝的文件
拷贝文件到hdd目录下
sudo cp /media/guest-mjsfmu/Windows/拷贝的文件/home/work/hdd
   拷贝完成，查看文件
work@localhost:~/hdd$ll -h

#9.ssh 服务端口是多少,ssh免密登录方式的原理是什么
/etc/ssh/sshd_config
默认服务端口Port 22
1.在A上生成公钥私钥。
2.将公钥拷贝给B，要重命名成authorized_keys(从英文名就知道含义了)
3.A向B发送一个连接请求。
4.B得到A的信息后，在authorized_key中查找，如果有相应的用户名和IP，则随机生成一个字符串，并用Server A的公钥加密，发送给A。
5. A得到B发来的消息后，使用私钥进行解密，然后将解密后的字符串发送给B。 B进行和生成的对比，如果一致，则允许免登录。
总之：A要免密码登录到B，B首先要拥有A的公钥，然后B要做一次加密验证。对于非对称加密，公钥加密的密文不能公钥解开，只能私钥解开。


#10.权限755代表什么权限,如果我想把所有的w权限去除应该使用什么命令
文件权限为755（二进制）
1、第一位7，代表文件所有者拥有的权限为可读（4）+可写（2）+可执行（1）
2、第二位5，代表文件所有者同组用户的权限为可读（4）+不可写（0）+可执行（1）
3、第三位5，代表公共用户的权限为可读（4）+不可写（0）+可执行（1）
去除所有w权限
chmod u-w,g-w,o-w 文件名字
#1.2

#1.git add和git stage的区别是什么

#2.git rm --cached 和git rm -f的区别是什么
当我们需要删除暂存区或分支上的文件, 但本地又需要使用, 只是不希望这个文件被版本控制, 可以使用git rm --cached 
直接删除文件不提醒git rm -f

#3.git和svn的区别是什么
svn收费与git不收费
Git是分布式的，SVN不是
GIT把内容按元数据方式存储，而SVN是按文件：
GIT分支和SVN的分支不同：
GIT没有一个全局的版本号，而SVN有
GIT的内容完整性要优于SVN：
GIT的内容存储使用的是SHA-1哈希算法。这能确保代码内容的完整性，确保在遇到磁盘故障和网络问题时降低对版本库的破坏。

#4.筛选出 2018.10.1 到 2018.10.20之间的日志,并且输出为地理图,并且没有做过合并
git log --after="2018-10-01 00:00:00" --before="2018-10-20 23:59:59"

#5.git init和git clone的区别
git init初始化本地的仓库，会生成.git文件，此时不会加入任何文件的快照
git clone克隆远程仓库到当前文件夹，会一起克隆远程的文件夹

#6.每次提交都忽略.idea文件夹里面的东西怎么办

#7.如果编辑一个文件之后并且加入了暂存区,但是你后悔了,想把文件恢复到没有修改之前的样子,怎么办
git log命令，用来查看我们提交的历史记录
进行版本回退，首先HEAD指的是当前版本，HEAD^是上一版本，HEAD^^是上上版本，如果是n次前的版本，应当是HEAD~n，我们可以用git reset命令来完成版本回退，现在输入git reset --hard HEAD~n
回到最初版本


#8.如何检出标签?
使用命令git tag，可以查看所有标签。如果要定义标签，只需要在git tag后添加要定义的标签名。例如：git tag v1.0.0。
git checkout -b [分支名] [标签名]

#9.git fetch 和 git pull的区别
git fetch (拉去最新远程分支版本)不需要指定分支
git pull(拉去最新远程分支版本并且做合并)

#10.如何添加远程仓库
GitHub 新建项目
git clone 项目地址
git add .
git commit -m ""







