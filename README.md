����code 
===========================
code�Ǻ���Ҫ��----ʹ��uliwebzone���̳

Ϊ�˱��ֺͷ�����ͬ����
1.���SVN���ذ�װuliwebzone������uliweb,plugs
svn checkout http://uliweb.googlecode.com/svn/trunk/ uliweb
svn checkout http://plugs.googlecode.com/svn/trunk/ plugs
cd uliweb
sudo python setup.py install
cd ../plugs
sudo python setup.py install
2. ��װuliwebzone
git clone https://github.com/limodou/uliwebzone.git
3.�޸�����uliwebzone
cd uliwebzone
3.1 ������ݿ�����
[ORM]
CONNECTION='mysql://root:rootpassword@localhost/uliweb?charset=utf8'
3.2 ���sessionĿ¼
[SESSION_STORAGE]
data_dir = '/var/www/xxxxxxxx/uliwebzone/sessions'
[CACHE_STORAGE]
data_dir = '/var/www/xxxxxxxx/uliwebzone/caches'
4.���ݿ�
4.1�������ݿ�
mysql -u root -p
create database uliweb
4.2 ������
��ʼ�����ݿ�
uliweb syncdb
4.3 ��������Ա
uliweb createsuperuser
4.4 ������ɫ
uliweb dbinit  uliweb.contrib.rbac
5.

����sessions,caches Ŀ¼��
cd /var/www/xxxx/uliwebzone/
mkdir sessions
mkdir caches
chmod 777 seesions caches
[UPLOAD]
TO_PATH = '/var/www/xxxx/uliwebzone/uploads'
[PARA]
FORUM_REPLY_PROCESS = 'noprint'
6.
����uliweb runserver
������� apache
uliweb.conf
WSGIScriptAlias /  /var/www/xxxx/uliwebzone/wsgi_handler.py

����apache������

7.ʹ�ó����û���¼������
