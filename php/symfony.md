# Symfony

* 'Symfony is just a set of services and routes'
* The container's job is to instantiate services
* autowiring works for constructor and controller function calls
* use ./bin/console about to see all environment variables, and other info
* require maker bundle for cool things like making commands `composer require maker --dev`
* then create command with `php bin/console make:command` and create class with given command name

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

* learn more about a service by: bin/console debug:container monolog.logger <service name>

## Environments
* APP_ENV logic is is config/bootstrap.php
* see order of config files loaded in Kernal.php
* all files in config either config services or routes
* change to prod in .ENV file

## Logging
* symfony uses monolog service for logging
* different categories of logging are called 'channels'
* If you want to pass a different service than autowire passes, configur ethis in config/services.yaml, specifying what gets passed to service parameter, with '@servicename' to pass service with this id

## config
* The reusable service id is snake case, local services have same id as class name 
* in services.yaml, use bind: $someParamName to pass given service whenever it is called
* in defaults, configs are project wide
* create 'parameters' or variables in yaml config files. 
* order of config file loading matters!
* ./bin/console debug:container --parameters => prints config variables
