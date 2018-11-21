#查询IP地址：
		Ip addr

	1. 换源命令：
			i. curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
		
			i. Yum makecache
		###查询IP地址：ip addr
----
#Web服务器的安装
----


	1. 换源命令：
			i. curl -o /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo
		
			i. Yum makecache
		
	2. 装Apache服务：
			i. Yum  install  httpd
		
	3. 打开httpd服务：
			i. Systemctl  start  httpd.service
		
	4. 设置开机启动：
			i. Systemctl  enable  httpd.service
		
	5. 防火墙放行80端口：
			i. Firewall -cmd  --add-port=80/tcp  (暂时性)
			ii. Firewall -cmd  --add-port=80/tcp  --permanent (永久性)
		
			i. Firewall -cmd  --list-all  (查询服务)
		
	6. PHP安装：
			i. Yum  -y  install  php-*  --skip-broken  php-mysqlnd     
			ii. //安装php全家桶，由于mysqlnd插件冲突会和mysql插件冲突，所以跳过
		
			i. Systemctl  restart  httpd.service
		
			i. 探针测试：
			ii. Cd  /var/www/html/
			iii. Wget  http://mirrors.eagleslab.com:8889/tz.php   (下载探针)  //请自行百度找探针下载
			Or
			Nano  test.php
				1) <?php
					a) phpinfo();
				2) ?>
			（保存后退出）
			打开网页http://<IP地址>//test.php 或者 tz.php
		
		
		
	7. 数据库安装：
			i. Yum  -y  install  mariadb*       
			ii. Systemctl  start  mariadb.service
			iii. Systemctl  enable  mariadb.service
			iv. Mysql_secure_installation
			        //初始化数据库（初始化密码为空，后面自己设置新密码）
		
			i. 验证是否成功
				尝试本地登录
				[root@localhost html]# mysql -uroot -p
				Enter password: 
				Welcome to the MariaDB monitor.  
				MariaDB [(none)]> quit
				Bye
				[root@localhost html]# 
			ii.     or
				登陆探针页面有mysql检测
			
			
	8. phpMyAdmin安装：
			yum install epel-release
			rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
			i. Cd  /var/www/html
			ii. Mkdir  phpmyadmin
			iii. Cd  phpmyadmin
			iv. yum install phpmyadmin
			
			vi. 验证
				1) 访问http://<IP地址>//phpmyadmin

				
				
#  博客系统的搭建
---------

	1. 新建数据库  blog
	
	2. 部署typecho
		a. Cd  /var/www/html
		b. Wget  http://mirrors.eagleslab.com:8889/typecho.zip   //百度找typecho下载  然后用rz上传至Linux
		c. Unzip  typecho.zip
		d. Chmod  -R  777  ../html      //给html下的所有子目录都给权限
		e. 验证是否成功
			i. 访问http://<IP地址>
			ii. 进入后网站初始化
				1) 数据库密码填新设置的
				2) 数据库名填blog(自己设置的)
				
	
	3. 用隧道打通到公网上
		a. 下载ngrok的客户端到本地
		b. 上传该客户端至服务器根目录
		c. 解压该目录
		d. 到客户端目录中给权限  chmod  777  sunny
		e. ngrok启动 ./sunny clientid 隧道id
		f. 打开typecho后台修改域名地址
		

	2. 装Apache服务：
			i. Yum  install  httpd
		
	3. 打开httpd服务：
			i. Systemctl  start  httpd.service
		
	4. 设置开机启动：
			i. Systemctl  enable  httpd.service
		
	5. 防火墙放行80端口：
			i. Firewall -cmd  --add-port=80/tcp  (暂时性)
			ii. Firewall -cmd  --add-port=80/tcp  --permanent (永久性)
		
			i. Firewall -cmd  --list-all  (查询服务)
		
	6. PHP安装：
			i. Yum  -y  install  php-*  --skip-broken  php-mysqlnd     
			ii. //安装php全家桶，由于mysqlnd插件冲突会和mysql插件冲突，所以跳过
		
			i. Systemctl  restart  httpd.service
		
			i. 探针测试：
			ii. Cd  /var/www/html/
			iii. Wget  http://mirrors.eagleslab.com:8889/tz.php   (下载探针)  //请自行百度找探针下载
			Or
			Nano  test.php
				1) <?php
					a) phpinfo();
				2) ?>
			（保存后退出）
			打开网页http://<IP地址>//test.php 或者 tz.php
		
		
		
	7. 数据库安装：
			i. Yum  -y  install  mariadb*       
			ii. Systemctl  start  mariadb.service
			iii. Systemctl  enable  mariadb.service
			iv. Mysql_secure_installation
			        //初始化数据库（初始化密码为空，后面自己设置新密码）
		
			i. 验证是否成功
				尝试本地登录
				[root@localhost html]# mysql -uroot -p
				Enter password: 
				Welcome to the MariaDB monitor.  
				MariaDB [(none)]> quit
				Bye
				[root@localhost html]# 
			ii.     or
				登陆探针页面有mysql检测
			
			
	8. phpMyAdmin安装：
			yum install epel-release
			rpm -ivh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm
			i. Cd  /var/www/html
			ii. Mkdir  phpmyadmin
			iii. Cd  phpmyadmin
			iv. yum install phpmyadmin
			
			vi. 验证
				1) 访问http://<IP地址>//phpmyadmin

				
				
#博客系统的搭建


	1. 新建数据库  blog
	
	2. 部署typecho
		a. Cd  /var/www/html
		b. Wget  http://mirrors.eagleslab.com:8889/typecho.zip   //百度找typecho下载  然后用rz上传至Linux
		c. Unzip  typecho.zip
		d. Chmod  -R  777  ../html      //给html下的所有子目录都给权限
		e. 验证是否成功
			i. 访问http://<IP地址>
			ii. 进入后网站初始化
				1) 数据库密码填新设置的
				2) 数据库名填blog(自己设置的)
				
	
	3. 用隧道打通到公网上
		a. 下载ngrok的客户端到本地
		b. 上传该客户端至服务器根目录
		c. 解压该目录
		d. 到客户端目录中给权限  chmod  777  sunny
		e. ngrok启动 ./sunny clientid 隧道id
		f. 打开typecho后台修改域名地址
		
