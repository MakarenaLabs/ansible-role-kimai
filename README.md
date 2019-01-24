<p align="center">
  <img width="150" height="150" src="https://www.saashub.com/images/app/service_logos/9/daeedc2e8541/large.png?1527968427">
</p>

# Ansible Role: Kimai
[![Build Status](https://travis-ci.org/MakarenaLabs/ansible-role-wordpress.svg?branch=master)](https://travis-ci.org/MakarenaLabs/ansible-role-kimai)
[![License](https://img.shields.io/github/license/MakarenaLabs/ansible-role-kimai.svg)](https://opensource.org/licenses/MIT)
[![Ansible Version](https://img.shields.io/badge/ansible-%3E%3D_1.4-8892BF.svg)](https://www.ansible.com/)


Ansible role that installs and configures Kimai with Nginx or Apache2 as webserver and MariaDB or MySQL as database service.

Features include:
- Installation of Kimai to specified domain
- Configuration of Nginx or Apache configuration file

## Installation

Using `ansible-galaxy`:
```shell
$ ansible-galaxy install makarenalabs.kimai
```

Using `arm` ([Ansible Role Manager](https://github.com/mirskytech/ansible-role-manager/)):
```shell
$ arm install makarenalabs.kimai
```

Using `git`:
```shell
$ git clone https://github.com/MakarenaLabs/ansible-role-kimai.git
```

## Requirements & Dependencies
- Ansible 1.4 or higher

## Variables
Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```yaml
k_dbserver: mariadb
ondrej_php: 'no'
php_version: 7.0
k_webserver: nginx
k_serveradmin: info@example.com
k_domainname: example.com
k_mysql_root_user: root
k_mysql_root_password: hackme
k_mysql_user: kimai
k_mysql_password: hackme
```
 - ```k_domainname```
 - ```k_mysql_user```
 - ```k_mysql_password```
 - ```k_mysql_root_user```
 - ```k_mysql_root_password```

These variables are required!

Default webserver selected is ```nginx```. If you want to use ```apache2``` you have to set ```k_webserver``` variable as follow:
```yaml
k_webserver: apache
```
Default database manager is ```mariadb```, but you can choose ```mysql``` setting ```k_dbserver``` as follow
```yml
k_dbserver: mysql
```
If you want to use a specific version of ```php``` that is present in Ondrej PHP ppa source, you just change value of variable ```ondrej_php``` and specify your PHP version
```yml
ondrej_php: 'yes'
php_version: X.X
```
By default, PHP version used in this role is ```7.0```.

## Example playbook
```yaml
---
- hosts: all
  vars:
    - k_domainname: example.com
    - k_mysql_user: kimai
    - k_mysql_password: hackme
    - k_mysql_root_user: root
    - k_mysql_root_password: hackme
  roles:
    - makarenalabs.kimai
```

## Testing
```shell
$ git clone https://github.com/MakarenaLabs/ansible-role-kimai.git
$ cd ansible-role-kimai
$ vagrant up
```

## License

Licensed under the MIT License. See the LICENSE file for details.

Copyright © 2019 [MakarenaLabs](https://www.makarenalabs.com)
