---
layout: post
title:  "Ubuntu下安装PHP+Apache+MySQL+phpmyadmin环境"
date:   2014-03-19 19:20:00
categories: 
- Notes 
tags:
- linux
- PHP
- Apache
- MySQL

---

最近开始用Ubuntu系统，想在这个系统上配置一套php服务器环境，但是又不想下载LAMP这个集成包，所以就试着逐一安装。

## Step 1: 安装 Apache
---

_1._ 启动终端程序。  
_2._ 输入以下命令：  
{% highlight sh %}
		sudo apt-get install apache2
{% endhighlight %}  
_3._ 输入密码后回车；  
_4._  安装完成后，在控制台中输入以下命令重启apache
{% highlight sh %}
		sudo service apache2 restart
{% endhighlight %}  
_5._  打开浏览器，输入`127.0.0.1`,页面显示apache主页，表明安装成功  
_6._  对于Web根目录，可以在配置文件中设置：
{% highlight sh %}
		vi /etc/apache2/sites-enabled/000-default
{% endhighlight %}
_7._  文件内的DocumentRoot后的目录就是根目录，设置为

		/var/www

## Step 2: 安装 PHP
---

_1._ 在控制台中输入：
{% highlight sh %}
	sudo apt-get install libapache2-mod-php5 php5 
{% endhighlight %}
_2._ 安装成功后，重启apache：
{% highlight sh %}
	sudo service apache2 restart
{% endhighlight %}   
_3._ 在之前的`/var/www`目录下建立一个`test.php`文件：
{% highlight php %}
<?php 
	phpinfo(); 
?>
{% endhighlight %}
然后在浏览器里输入`127.0.0.1/test.php`，测试PHP是否能正常运行。

## Step 3: 安装 MySQL
---

_1._ 在控制台中输入：
{% highlight sh%}
	sudo apt-get install mysql-server mysql-client
{% endhighlight %}
_2._ 安装时会让设置root帐号的密码，输入密码即可。

## Step 4: 安装phpmyadmin
---

_1._ 在控制台中输入：
{% highlight sh%}
	sudo apt-get install phpmyadmin
{% endhighlight %}
_2._ 在安装时选择web server为`apache2`。  
_3._ 安装好后，需要将phpmyadmin的目录链接到apache的根目录下：
{% highlight sh%}
	sudo ln -s /usr/share/phpmyadmin /var/www
{% endhighlight %}

至此安装完毕。




