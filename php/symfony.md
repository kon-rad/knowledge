

# Bundles
* Bundles are a plugin system in Symfony.
* Services are tools in symfony, which come in bundles. 
* Everything in symfony is done by a service.
* Bundles give us these services. Installing more bundles gives more services.

* run bin/console debug:autowiring to see list of services

* List of bundles is found in config/bundles.php file.

* internally each service has a unique name or id, just like routes, for example, cache.app is for Symfony's internal cache servicerequire