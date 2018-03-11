[![Build Status](https://travis-ci.org/while-true-do/ansible-role-php.svg?branch=master)](https://travis-ci.org/while-true-do/ansible-role-php)

# Ansible Role: PHP
| A role that installs PHP on the target system.

## Motivation

PHP is needed for a lot of web-based applications, e.g. Nextcloud, WordPress.

## Installation

Install from [Ansible Galaxy](https://galaxy.ansible.com/while-true-do/php)

```
ansible-galaxy install while-true-do.php
```

Install from [Github](https://github.com/while-true-do/ansible-role-php)

```
git clone https://github.com/while-true-do/ansible-role-php.git while-true-do.php
```

## Requirements

Used Modules:

-   [file_module](http://docs.ansible.com/ansible/latest/file_module.html)
-   [include_tasks_module](http://docs.ansible.com/ansible/latest/include_tasks_module.html)
-   [include_vars_module](http://docs.ansible.com/ansible/latest/include_vars_module.html)
-   [package_module](http://docs.ansible.com/ansible/latest/package_module.html)
-   [service_module](http://docs.ansible.com/ansible/latest/service_module.html)
-   [template_module](http://docs.ansible.com/ansible/latest/template_module.html)

## Dependencies

This role depends on [while-true-do.repo-webtatic](https://galaxy.ansible.com/while-true-do/repo-webtatic). You have to install the role:
```
ansible-galaxy install -r requirements.yml
```

## Role Variables

```yaml
# defaults/main.yml for php

wtd_php_fpm_enable: false

wtd_php_fpm_user: "apache"
wtd_php_fpm_group: "apache"
wtd_php_fpm_listen: "127.0.0.1:9000"
wtd_php_fpm_env_hostname: "$HOSTNAME"
wtd_php_fpm_env_path: "/usr/local/bin:/usr/bin:/bin"
wtd_php_fpm_env_tmp: "/tmp"
wtd_php_fpm_env_tmpdir: "/tmp"
wtd_php_fpm_env_temp: "/tmp"

wtd_php_repository: "default"
```

```yaml
# vars/CentOS.yml

wtd_php_fpm_service: "php-fpm"
```

```yaml
# vars/CentOS-default.yml

wtd_php_packages:
  - php

wtd_php_fpm_packages:
  - php-fpm
```

```yaml
# vars/CentOS-webtatic.yml

wtd_php_packages:
  - php71w-common
  - php71w-cli

wtd_php_fpm_packages:
  - php71w-fpm
```

## Example Playbook

Simple Example:

```yaml
- hosts: servers 
  roles:
    - { role: while-true-do.php }
```

Advanced Example:

```yaml
- hosts: servers 
  roles:
    - { role: while-true-do.php, wtd_php_fpm_enable: true, wtd_php_repository: "webtatic" }
```

## Testing

All tests are located in [test directory](./tests/).

Basic testing:

```
bash ./tests/test-spelling.sh
bash ./tests/test-ansible.sh
```

## Contribute / Bugs

Thank you so much for considering to contribute. Every contribution helps us.
We are really happy, when somebody is joining the hard work. Please have a look 
at the links first.

-   [Contribution Guidelines](./docs/CONTRIBUTING.md)
-   [Create an issue or Request](https://github.com/while-true-do/ansible-role-php/issues)
-   [See who was contributing already](https://github.com/while-true-do/ansible-role-php/graphs/contributors)

## License

This work is licensed under a [BSD License](https://opensource.org/licenses/BSD-3-Clause).

## Author Information

Blog: [blog.while-true-do.org](https://blog.while-true-do.org)

Mail: [hello@while-true-do.org](mailto:hello@while-true-do.org)
