# My Code Styles Guide
================

> Ninety percent of these styles will follow the best practices recommended worldwide, with some highlights in specific points that i altered..

## Important Details

The following document describes the rules of writing in development languages that I use: PHP, HTML, CSS, JavaScript, etc...

The idea of this repository is be a complete code guide. For myself and other developers who participate in my projects follow the same coding pattern.

#### This is a live document and changes can occur at any time, for this reason I recommend that from 'watching' in this repository.

###### *As this is a new document, some rules may not have been applied in old projects.

<hr>

## Summary

> Here are some previews of the style. Click in the link to go complete guide.

- [PHP Code Style]()
```php
<?php namespace System\Core\Loaders;

/*
 ===========================================================================
 = Preview About Class Content
 ===========================================================================
 =
 = Brief description about functionality of class...
 = 
 */

use \System\IO\FileReader;
use \package\subpackage\IRunnable;
use \RuntimeException;

/**
 * PHPDoc of Class
 * ...
 */
class LoggerBoot extends FileReader implements IRunnable
{
    /**
     * The status of reading file
     * @var boolean
     */
    private $status = false;
    
    /**
     * File title for search
     * @var string
     */
    private $file = '';
   
    /**
     * Path for files dir
     * @var string
     */
    private $path = ROOT_APP_JOYN;
    
    /**
     * For variables in same group define the equals aligned
     * @var array
     */
    private $sometinhg       = [];
    private $otherSomething  = [];
    private $theExampleVar   = [];
    
    /**
     * Function for sintaxe example
     * @param string [optional desc]
     * @param boolean [optional desc]
     * @return void 
     */
    public function example($file, $status = false)
    {
        if(condition..):
            //Code here...
        endif;
	
        for(loop..):
            //Code here...
        endfor;
	
        switch(var..):
            //Code here...
        endswitch;
	
        //etc...
	
    }
    
}

```

- [HTML Code Style]()
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="author" content="lleocastro"/>
  <meta name="description" content="HTML structure example for my style guide"/>
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <meta name="robots" content="index, follow"/>

  <link rel="icon" type="image/png" href="assets/logo.png"/>
  <link rel="stylesheet" href="css/example.css"/>
	
  <title>HTML Structure Example</title>
</head>
<body>
  <main>
    <p>Hello World!</p>
  </main>
</body>
</html>
```

- [CSS Code Style]()
```css
<!-- ... -->
```

- [JS Code Style]()
```js
//...
```


## To contributions 

Please, see [doc for contribute](https://github.com/lleocastro/styles-guide/blob/master/CONTRIBUTE.md). Thanks!


### License

That Style guide is licensed under the MIT license. See [License File](https://github.com/lleocastro/styles-guide/blob/master/LICENSE) for more information.
