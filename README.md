Yii2 Oracle Oci8 Driver 
=======================

Installation
------------

### Install With Composer

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require titanium_iridium/yii2-oci8 "dev-master"
```

or add

```
"titanium_iridium/yii2-oci8": "dev-master"
```

to the require section of your `composer.json` file.

### OR Install From Archive
You can also install from archive. Add aliase on config file to point alias to the folder
```
return [
    ...
    'aliases' => [
        '@titanium_iridium/oci8' => 'path/to/your/extracted',
        ...
    ]
];
```

Usage
-----

Once the extension is installed, simply modify your application configuration on main-local.php as follows :

```
return [	
	'components' => [
		....
		'db' => [
                    'class' => 'titanium_iridium\oci8\Oci8DbConnection',
                    'dsn' => 'oci8:dbname=(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)(HOST=127.0.0.1)(PORT=1521))(CONNECT_DATA=(SID=xe)));charset=AL32UTF8;',
                    'username' => 'yourdatabaseschemaname',
                    'password' => 'databasepassword',
                    'attributes' => []
                ],
	],
];
```
Custom User's Table Migration
---------------------------

You may want to create user's table using migration command. Instead of using yii default migrate (yii migrate), specify the custom migrationPath to point to custom user's table migration to avoid oracle error ('ORA-00907: missing right parenthesis). 
Note: you have to manually add user's table sequence eg. user_seq on you oracle db  and primary key trigger using sql developer or toad.

```
yii migrate --migrationPath=@titanium_iridium/oci8/migrations
```
You can refer the sample application using yii2 advance template here titanium_iridium/yii2-php7-oci8 https://github.com/titanium_iridium/yii2-php7-oci8
