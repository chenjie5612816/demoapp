关于code 
===========================
code是很重要的----使用uliwebzone搭建论坛

为了保持和服务器同步：
1.请从SVN下载安装uliwebzone依赖：uliweb,plugs
svn checkout http://uliweb.googlecode.com/svn/trunk/ uliweb
svn checkout http://plugs.googlecode.com/svn/trunk/ plugs
cd uliweb
sudo python setup.py install
cd ../plugs
sudo python setup.py install
2. 安装uliwebzone
git clone https://github.com/limodou/uliwebzone.git
3.修改配置uliwebzone
cd uliwebzone
3.1 添加数据库配置
[ORM]
CONNECTION='mysql://root:rootpassword@localhost/uliweb?charset=utf8'
3.2 添加session目录
[SESSION_STORAGE]
data_dir = '/var/www/xxxxxxxx/uliwebzone/sessions'
[CACHE_STORAGE]
data_dir = '/var/www/xxxxxxxx/uliwebzone/caches'
4.数据库
4.1创建数据库
mysql -u root -p
create database uliweb
4.2 创建表
初始化数据库
uliweb syncdb
4.3 创建管理员
uliweb createsuperuser
4.4 创建角色
uliweb dbinit  uliweb.contrib.rbac
5.

创建sessions,caches 目录：
cd /var/www/xxxx/uliwebzone/
mkdir sessions
mkdir caches
chmod 777 seesions caches
[UPLOAD]
TO_PATH = '/var/www/xxxx/uliwebzone/uploads'
[PARA]
FORUM_REPLY_PROCESS = 'noprint'
6.
启动uliweb runserver
或者添加 apache
uliweb.conf
WSGIScriptAlias /  /var/www/xxxx/uliwebzone/wsgi_handler.py

重启apache服务器

7.使用超级用户登录。。。
#补充内容
安装uliweb和plugs时，可以使用:

python setup.py develop

这样的一个好处是：并不会拷贝文件到site-packages下，而只是建一个链接。同时以后如果版本不升级，只要svn update即可。

##补充
另外uliweb, plugs在git上都有项目。

这里好象没考虑把静态文件让web server来处理。uliweb提供uliweb exportstatic outputdir的命令，可以导出所有的静态文件。

另，MySQL的文本字段(TEXT)缺省只能支持64K大小，所以如果贴子过长，想支持更大的，可以直接修改数据库中的大小，如：

ALTER TABLE forumpost modify column `content` mediumtext;

##补充2
Simple Todo (Uliweb 版本) 之 基础篇
Simple Todo (Uliweb 版本) 之 高级篇
Hello, Uliweb
迷你留言板
Sina Application Engine部署及开发指南
Baidu Application Engine部署及开发指南
Heroku 部署说明
