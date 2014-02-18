# Virtual Machine for PHP development

Virtual machine suitable for PHP development (Symfony, Laravel, Drupal 8, etc).
Build with Debian 7.x (Wheezy) including Nginx, MySQL, PHP-FPM and more packages.

## Requirements

- VirtualBox: https://www.virtualbox.org/wiki/Downloads
- Vagrant: http://downloads.vagrantup.com/

## Avaiable Roles

- Java (openJDK)
- MailCatcher
Set your favourite app to deliver to smtp://127.0.0.1:1025 instead of your default SMTP server, then check out
http://127.0.0.1:1080 to see the mail that's arrived so far.
- Memcached
- MySQL
Uses the custom.ini from provisioning/roles/mysql/templates to override the default settings
- NodeJs
- Redis
Uses the config from provisioning/roles/redis/templates/redis.conf.j2
- PHP-FPM
Uses the config files from provisioning/roles/php-fpm/templates
- Nginx
- Zend-Server
Can't be used with the roles PHP-FPM and Nginx!

## Configuration
- Vagrantfile
This file contains a config options array which you can change, or create a Vagrantfile.local with the config options
you want to override.

- provisioning/group_vars/all
This file contains all configuration variables for the available roles.

- provisioning/playbook.yml
Enable the roles you need by removing the # in front of the line or place a # in front of a role to disable it

## Usage
Copy the Vagrantfile and provisioning directory to your project, update the configuration and type:
```
vagrant up
```

## Todo
- Make PHP Timezone configurable, currently hardcoded to Europe/Amsterdam
- Add vhost to Zend-Server



##  License

This code is open-sourced software licensed under the
[MIT license](http://opensource.org/licenses/MIT)
