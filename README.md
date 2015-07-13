# Constructor

Specilized PHP Scaffolding Constructor.

## Definitions

- blueprint - The main generator script for generating scaffolding.
- facility  - Components that can be generated.
- postproduction - scripts that runs after generation.

## Generator File Structure

```
generators/controller/blueprint.php      // the main control script for generating stuff...
generators/controller/dependencies.php   // the generator dependencies
generators/controller/postproduction.php // for hanlding post-initialization
generators/controller/facilities/route/route.php
generators/controller/resources/templates/

generators/schema/blueprint.php
generators/schema/facilities/model/...
generators/schema/facilities/collection/...
generators/schema/facilities/repository/...
generators/schema/resources/assets/images/...
generators/schema/resources/assets/js/...

generators/action/blueprint.php
```

## API Synopsis

```php
$loader = new Construct\GeneratorLoader([ 
  'directory' => [ .... ]
]);
$generators = $loader->search('/some pattern/');
$generator = $loader->load('controller');
$generator->generate([  
  ....
]);
```






