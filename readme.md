Better CodeIgniter Config
=========================

My branch of CodeIgniter provides better support for multi-environment configuration.
The normal version of CodeIgniter expects you to put all the configuration values into every configuration file.
Other systems like Zend Framework and Symfony have systems that allow configuration to be extended from one environment to another.
With my version of CodeIgniter you now have a similar capability.

Example main database config
----------------------------
**application/config/database.php**

```php
$active_group = 'default';
$active_record = TRUE;

$db['default']['hostname'] = 'localhost';
$db['default']['username'] = 'db_pass';
$db['default']['password'] = 'db_user';
$db['default']['database'] = 'my_app';
$db['default']['dbdriver'] = 'mysql';
$db['default']['dbprefix'] = '';
$db['default']['pconnect'] = TRUE;
$db['default']['db_debug'] = TRUE;
$db['default']['cache_on'] = FALSE;
$db['default']['cachedir'] = '';
$db['default']['char_set'] = 'utf8';
$db['default']['dbcollat'] = 'utf8_general_ci';
$db['default']['swap_pre'] = '';
$db['default']['autoinit'] = TRUE;
$db['default']['stricton'] = FALSE;
```

Example dev database config
---------------------------
With my branch of CodeIgniter, you only have to override variables from the main configuration that are different in the new environment.

**application/config/development/database.php**
```php
$db['default']['hostname'] = 'db.myapp.com';
$db['default']['username'] = 'prod_db_pass';
$db['default']['password'] = 'prod_db_user';
$db['default']['database'] = 'my_app';
```

Notes
-----

This works for any configuration file

1. main configuration file, **application/config.php**
2. core configuration files **application/config/database.php**, **application/config/routes.php**
3. custom configuration files **application/config/custom.php**


There may be other system components that aren't using the standard configuration system. I've already had to port the database and routing components. I'll plan to do a more exhaustive search of the code and ensure every place loading configuration uses the standard system.

