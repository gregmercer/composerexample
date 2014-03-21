composerexample
===============

Composer Example


Add this to your vhosts.conf file
```
	<VirtualHost *>
	  ServerName composerexample.localhost
	  DocumentRoot "/Users/macgmercer/Sites/composerexample"
	  <Directory "/Users/macgmercer/Sites/composerexample">
	    Options Indexes FollowSymLinks
	    AllowOverride All
	    Order allow,deny
	    Allow from all
	  </Directory>
	</VirtualHost>
```	

...

Add this to your hosts file - /etc/hosts
```
	127.0.0.1 composerexample.localhost
```

...

Create a site folder
```
	/Users/macgmercer/Sites/composerexample
```	

...

Create a .htaccess file - /Users/macgmercer/Sites/composerexample/.htaccess
```
	RewriteEngine On

	# Some hosts may require you to use the `RewriteBase` directive.
	# If you need to use the `RewriteBase` directive, it should be the
	# absolute physical path to the directory that contains this htaccess file.
	#
	# RewriteBase /

	RewriteCond %{REQUEST_FILENAME} !-f
	RewriteRule ^ index.php [QSA,L]	
```

...

Install composer in your project:
```
	cd /Users/macgmercer/Sites/composerexample
	curl -s https://getcomposer.org/installer | php
```

Create a composer.json file in your project folder - /Users/macgmercer/Sites/composerexample/composer.json
```
	{
	    "require": {
	        "doctrine/inflector": "1.0.*"
	    }
	}
```

Install via composer:
```
	cd /Users/macgmercer/Sites/composerexample
	php composer.phar install
```

Create index.php - /Users/macgmercer/Sites/composerexample/index.php
```
	<?php

	$loader = require 'vendor/autoload.php';

	use Doctrine\Common\Inflector\Inflector;

	$singular = 'mouse';
	$plural = Inflector::pluralize($singular);

	print 'The plural of ' . $singular . '  is ' . $plural . '. Squeek(s)!';
```
...

Restart your apache server


	
