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
generators/controller/instructions.php   // built-in instructions
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

### blueprint.php

```php
<?php

class ControllerBlueprint extends Blueprint 
{


    /**
     * Triggered before generating stuff...
     */
    public function prepare() {  }


    /**
     * The main generator logics
     */
    public function generate() 
    {
        // Some built-in instructions

        // Run composer install
        composer_install([  ... ]);

        // Run composer update
        composer_update([ ... ]);

        // Adding composer requirements
        composer_require([ ... ]);

        // Updating composer.json for some fields
        composer_set( );




        // git clone as...
        git_clone('git://github.com/c9s/ActionKit', 'actionkit');
        git_add($files);
        git_add("src/*.php");

        // git commit files under src directory
        git_commit("src");

        move_files('*.php', ...);

        rename_files([ 
          'foo' => 'bar'
        ]);

        copy_files( 'templates' );

        render_files('...');

        install_resources('images' , $targetDir);
        install_resources('js' , $targetDir);
    }

    public function finish() 
    {

    }

}

// The returned variable at the end will be invoked
return new ControllerBlueprint(....);


// You can also return multiple blueprints objects
return [ new ControllerBlueprint(....), new ... ];
```




### GeneratorLoader

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






