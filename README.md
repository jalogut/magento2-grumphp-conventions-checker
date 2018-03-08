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
    - { resource: magento/vendor/jalogut/magento2-conventions-checker/magento2-project-grumphp.yml }
```

* Add the following scripts in your `composer.json`

```
  "scripts": {
    "grumphpInitProject": "[ ! -e bin/grumphp ] || [ ! -e magento/vendor/jalogut/magento2-conventions-checker ] || bin/grumphp git:init",
    "grumphpInitModules": "[ ! -e bin/grumphp ] || [ ! -e magento/vendor/jalogut/magento2-conventions-checker ] || find magento/vendor/<vendor>/* -type f -name grumphp.yml -maxdepth 1 -exec dirname {} \\; | xargs -I{} bash -c \"cd '{}' && ../../../../bin/grumphp git:init\"",
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
    - { resource: ../../jalogut/magento2-conventions-checker/magento2-module-grumphp.yml }
```

