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
