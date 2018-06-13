# Magento 2 Grumphp Conventions Checker

## Installation

```
composer require --dev "jalogut/magento2-grumphp-conventions-checker:^2.2"
```

### Project

* Create `grumphp.yml` file in the root folder with the following content:

```
parameters:
    magento_dir: <magento_dir>
    vendor_dir: <vendor_dir>
imports:
    - { resource: %vendor_dir%/jalogut/magento2-grumphp-conventions-checker/magento2-project-grumphp.yml }
```

* Add the following scripts in your `composer.json`

```
  "scripts": {
    "grumphpInitProject": "[ ! -e bin/grumphp ] || [ ! -e <vendor_dir>/jalogut/magento2-grumphp-conventions-checker ] || bin/grumphp git:init",
    "grumphpInitModules": "[ ! -e bin/grumphp ] || [ ! -e <vendor_dir>/jalogut/magento2-grumphp-conventions-checker ] || find <vendor_dir>/<company_vendor_name>/* -type f -name grumphp.yml -maxdepth 1 -exec dirname {} \\; | xargs -I{} bash -c \"cd '{}' && ../../../../bin/grumphp git:init\"",
    "pre-autoload-dump": [
        "mkdir -p <magento_dir>/app/etc && cp <vendor_dir>/magento/magento2-base/app/etc/NonComposerComponentRegistration.php <magento_dir>/app/etc/NonComposerComponentRegistration.php"
    ],
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

**NOTE**: replace `<vendor_dir>`, `<company_vendor_name>` and `<magento_dir>` according to your configuration

### Magento Common Module

* Create `grumphp.yml` file in the root folder with the following content:

```
parameters:
    magento_dir: <magento_dir>
    vendor_dir: <vendor_dir>
imports:
    - { resource: ../../jalogut/magento2-grumphp-conventions-checker/magento2-module-grumphp.yml }
```

**NOTE**: replace `<vendor_dir>` and `<magento_dir>` according to your configuration

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

