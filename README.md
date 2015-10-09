# PHP Development Machine


This a development machine for my php projects, mainly symfony2 or silex.

## Getting Started

Tune `vhosts/silex` or `vhosts/symfony` to your needs. The defaults assume you either
have a `symfony` or `silex` directory in your root.

Then you can just run `vagrant up` and everything will be setup for you.

### Requirements 

This requires you have ansible and nfs server installed. And of course, virtualbox and vagrant.

## Notes on Symfony

Symfony by default will not let you access `app_dev.php` from other then `localhost`, just
add `'10.0.2.2'` to the list of allowed hosts in `web/app_dev.php` like this:

```php
if (isset($_SERVER['HTTP_CLIENT_IP'])
    || isset($_SERVER['HTTP_X_FORWARDED_FOR'])
    || !(in_array(@$_SERVER['REMOTE_ADDR'], array('127.0.0.1', '10.0.2.2', 'fe80::1', '::1')) || php_sapi_name() === 'cli-server')
) {
    header('HTTP/1.0 403 Forbidden');
    exit('You are not allowed to access this file. Check '.basename(__FILE__).' for more information.');
}	
```


