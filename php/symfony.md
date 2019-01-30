# Symfony

* 'Symfony is just a set of services and routes'

## Bundles
* Bundles are a plugin system in Symfony.
* Services are tools in symfony, which come in bundles. 
* Everything in symfony is done by a service.
* Bundles give us these services. Installing more bundles gives more services.

* run bin/console debug:autowiring to see list of services

* List of bundles is found in config/bundles.php file.

* internally each service has a unique name or id, just like routes, for example, cache.app is for Symfony's internal cache servicerequire

* dump all config options for a bundle with bin/console config:dump <bundleName> KnpMarkdownBundle
* To overwrite bundle configs, add new file in config/packages
* to see the config of a bundle user ./bin/console config:dump <bundleName> framework
* to findout about configs for each bundle, see the docs
* in the config yaml files, the names of the files are not important, the important part is the root key, which tells which bundle is configured
* all configs are part of one config system, could be in one file 

## Environments
* APP_ENV logic is is config/bootstrap.php
* see order of config files loaded in Kernal.php
* all files in config either config services or routes
* change to prod in .ENV file
