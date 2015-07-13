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
generators/controller/scaffolding/__foo__/        // the directory structure under scaffolding directory will be created.
generators/controller/scaffolding/__bar__/        // identities wrapped with underscore can be replaced by variables.

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

  'my_class_name' => 'MyController',
  'my_extra_var'  => 'indexAction',

  // variables that will be applied to scaffolding structure 
  '__path_vars' => [
    '__foo__' => 'assets'
    '__bar__' => '',
  ],


], [  
  // generator options for dependencies
  'dependency1' => [ .... ],
  'dependency2' => [ .... ],
  'dependency3' => [ .... ],
]);
```






