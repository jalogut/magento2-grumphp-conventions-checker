# Magento 2 Grumphp Conventions Checker

## Installation

```
composer require --dev "jalogut/magento2-grumphp-conventions-checker:^2.2.0" \
    "phpro/grumphp": "^0.14" \
    "squizlabs/php_codesniffer": "~3.2.2" \
    "phpmd/phpmd": "^2.6"
```

### Project

* Create `grumphp.yml` file in the root folder with the following content:

```
imports:
    - { resource: magento/vendor/jalogut/magento2-grumphp-conventions-checker/magento2-project-grumphp.yml }
```

* Add the following scripts in your `composer.json`

```
  "scripts": {
    "grumphpInitProject": "[ ! -e bin/grumphp ] || [ ! -e magento/vendor/jalogut/magento2-grumphp-conventions-checker ] || bin/grumphp git:init",
    "grumphpInitModules": "[ ! -e bin/grumphp ] || [ ! -e magento/vendor/jalogut/magento2-grumphp-conventions-checker ] || find magento/vendor/<vendor>/* -type f -name grumphp.yml -maxdepth 1 -exec dirname {} \\; | xargs -I{} bash -c \"cd '{}' && ../../../../bin/grumphp git:init\"",
    "post-install-cmd": [
      "@grumphpInitProject",
      "@grumphpInitModules"
    ],
    "post-update-cmd": [
      "@grumphpInitProject",
      "@grumphpInitModules"
    ]
  }
```

### Magento Common Module

* Create `grumphp.yml` file in the root folder with the following content:

```
imports:
    - { resource: ../../jalogut/magento2-grumphp-conventions-checker/magento2-module-grumphp.yml }
```

## Prerequisites

- MAGENTO >= 2.2.2

## Developers

* [Juan Alonso](https://github.com/jalogut)
* [Contributors](https://github.com/jalogut/magento2-deployer-plus/graphs/contributors)

Licence
-------
[GNU General Public License, version 3 (GPLv3)](http://opensource.org/licenses/gpl-3.0)

Copyright
---------
(c) Juan Alonso <juan.jalogut@gmail.com>

