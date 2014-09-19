# razor install document

Cobub Razor - Open Source Mobile Analytics Solution 
http://dev.cobub.com


## install-requirements

假定mysql之前已经安装好了

其他参考

	http://dev.cobub.com/docs/cobub-razor/install-requirements/


## 安装php环境
卸载

	sudo apt-get --purge remove php5
	sudo apt-get --purge remove php5-common
	sudo apt-get --purge remove libapache2-mod-php5
	sudo apt-get --purge remove php5-cli
	sudo apt-get --purge remove apache2
	sudo apt-get --purge remove apache2-common
	sudo apt-get --purge remove apache2-utils



再安装

[ubuntu php install guide](http://php.net/manual/en/install.unix.debian.php)

我整理的命令

	sudo apt-get install apache2 php5-common libapache2-mod-php5 php5-cli php5-mysql php5-json

安装后测试

	➜  ~  php -v
	PHP 5.5.3-1ubuntu2.6 (cli) (built: Jul  7 2014 16:54:32) 
	Copyright (c) 1997-2013 The PHP Group
	Zend Engine v2.5.0, Copyright (c) 1998-2013 Zend Technologies
	    with Zend OPcache v7.0.3-dev, Copyright (c) 1999-2013, by Zend Technologies

即可


## 修改配置文件

	sudo vi /etc/php5/apache2/php.ini

把error_reporting对应的值改成

	error_reporting = E_ALL ^ E_DEPRECATED.
	
这样就可以避免安装时候mysqli和POD报错了。


## 重启apache2

sudo service apache2 restart


## 排错

时刻看着错误日志，以确定问题

	tail -f /var/log/apache2/error.log 

 
## 如果需要，安装phpmyadmin管理数据

### 安装命令

	sudo apt-get install phpmyadmin

### 设置

在安装过程中会要求选择Web server：apache2或lighttpd，选择apache2，按tab键然后确定。

然后会要求输入设置的Mysql数据库密码连接密码 Password of the database’s administrative user。

然后将phpmyadmin与apache2建立连接，以我的为例：www目录在/var/www，phpmyadmin在/usr/share/phpmyadmin目录，所以就用命令：

	sudo ln -s /usr/share/phpmyadmin /var/www 
	
建立连接。

### 测试地址

在浏览器地址栏中打开http://HOST:PORT/phpmyadmin

可用户登录即可


## 安装razor

- 项目地址 https://github.com/cobub/razor
- 安装文档 http://dev.cobub.com/docs/cobub-razor/

### Download Cobub Razor

最好是到项目地址里自己找安装包，保证最新稳定版本即可

### 讲安装包解压到/var/www/razor目录下

### 赋予相应权限

	chmod -R 777 /var/www/razor
	
### Setup Scheduled Task

详见 
	
	http://dev.cobub.com/docs/cobub-razor/auto-archiving/

### 在浏览器打开安装界面

	http://HOST:PORT/tongji/web/index.php?/install/installation/

按照步骤安装即可

### 使用

登录即可

	http://HOST:PORT/razor/web/index.php?/auth/login

## razor SDK

- [iOS Developer Guide](http://dev.cobub.com/docs/cobub-razor/ios-developer-guide/)
- [Android Developer Guide](http://dev.cobub.com/docs/cobub-razor/android-developer-guide/)
- [Windows Phone Developer Guide](http://dev.cobub.com/docs/cobub-razor/windows-phone-developer-guide/)


## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## 版本历史

- v0.1.0 初始化版本

## 欢迎fork和反馈

- write by `i5ting` shiren1118@126.com

如有建议或意见，请在issue提问或邮件

## License

this repo is released under the [MIT
License](http://www.opensource.org/licenses/MIT).

