# My Styles Guide for Codes
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
    <ul>
      <li>...</li>
      <li>...</li>
      <li>...</li>
    </ul>
    
    <section>
      <article>
        
        <header>
          <h1>...</h1>
          <p class= "tagline">...</p>
        </header>
	
        <!-- Content -->
	
        <footer>
	  ...
        </footer>	
      </article>
    </section>
    
  </main>
</body>
</html>
```

- [CSS Code Style]()
```css
@charset "UTF-8";
 
/* Reset CSS */
html {
  color: #333;
  font-family: "sans-serif", Arial, Helvetica;
  font-size: 16px;
  text-indent: 1px;
  font-weight: normal;
  text-align: left;
  vertical-align: baseline;
  background-color: #fff;
}

body {
  margin: 0;
  padding: 0;
}

header,
hgroup,
section,
article,
aside,
figcaption,
figure,
summary,
details,
nav,
div,
main,
footer,
input,
textarea {
  display: block;
  overflow: hidden;
  position: relative;
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
      -ms-box-sizing: border-box;
       -o-box-sizing: border-box;
          box-sizing: border-box;
}

img,
video,
embed {
  width: 100%;
  vertical-align: middle;
  border: 1px solid transparent;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  color: #454743;
  font-size: 2em;
}
p {
  color: #8C8C8C;
  font-size: 1em;
}
strong {
  font-weight: bold;
}
small {
  color: #777;
  font-size: 73%;
}
em { 
  font-style: italic;
}
code,
pre {
  font-family: monospace;
  font-size: 1em;
}

a { 
  color: #017fb5;
  text-decoration: none;
  background-color: transparent;
}

a,
button,
input,
optgroup,
select,
textarea {
  outline: 0;
}
button,
select,
input[type="button"],
input[type="submit"],
input[type="reset"] {
  text-transform: none;
}
a,
button,
input[type="button"],
input[type="submit"],
input[type="reset"] {
  cursor: pointer;
}
button[disabled],
input[disabled] {
  cursor: default;
}

ol,
ul {
  list-style: none;
}

table {
  border-spacing: 0;
  border-collapse: collapse;
}
td, 
th {
  padding: 0;
}
```

- [JS Code Style]()
```js
// Debug mode of the game
var debugMode = false;

// Immutable objects
var states = Object.freeze({
    splashScreen: 0,
    duringGame: 1,
    gameEnd: 2
});

//Physics of the game
var currentState;
var gravity = 0.25;
var velocity = 0;
var position = 180;
var rotation = 0;
var jump = -4.6;

//Pre-defined measures for pipes
var obstacle = new Array();
var obstacleWidth = 52;
var obstacleHeight = 90;

//Current score and best
var score = 0;
var bestScore = 0;

//Loops of iteration
var gameLoop;
var obstacleLoop;

//Reload game
var restart = false;

//Definition of sounds
var soundJump = new buzz.sound("assets/sounds/wing.ogg");
var soundScore = new buzz.sound("assets/sounds/point.ogg");
var soundHit = new buzz.sound("assets/sounds/hit.ogg");
var soundDie = new buzz.sound("assets/sounds/die.ogg");
var soundSwoosh = new buzz.sound("assets/sounds/swooshing.ogg");
buzz.all().setVolume(30);
/// End of variables declaration ///

/* 
    /// BUILDER ///
*/
$(document).ready(function(){
    // Init debug mode
    if(window.location.search == "?debug"){
		debugMode = true;
	}else if(window.location.search == "?easy"){
		obstacleHeight = 200;
	}

	// Get best score by cookie
	var savedScore = getCookie("bestScore");
	if(savedScore != ""){
		bestScore = parseInt(savedScore);
	}

	showSplashScreen();

});

$(document).keydown(function(e){    
    if(e.keyCode == 32){
        // Begins with the spacebar
        if(currentState == states.gameEnd){
            $("#restart").click();
        }else{
            stateGame();
        }
    }
});

// Begins with the touch or mouse
if("ontouchstart" in window){
    $(document).on("touchstart", stateGame);
}else{
    $("#modal").on("mousedown", stateGame);
}

// Initializes the game based on the current state
function stateGame(){
    if(currentState == states.duringGame){ 
        playerJump();
    }else if(currentState == states.splashScreen){ 
        startGame(); 
    }
}

/*
  /// INITIALIZES THE GAME ///
*/
function startGame(){
    currentState = states.duringGame;

    //Hide of splash screen
    $("#splash-screen").stop();
    $("#splash-screen").transition({ opacity: 0 }, 500, 'ease');

    //Update current score during game
    setScoreInGame();

    //Check border
    if(debugMode){ 
        $(".boundingbox").show(); 
    }

    //Loop interval
    gameLoop = setInterval(inLoop, (900.0 / 60.0)); // 60fps
    obstacleLoop = setInterval(addObstacle, 1400); // Sets the distance between obstacles

    //Start
    playerJump();
}

function inLoop(){
    //Upadate rate
    velocity += gravity;
    position += velocity;
    //Apply new rate
    updatePlayer($("#player"));

    //Creates the hack bounding box, for the personage
    var box = document.getElementById('player').getBoundingClientRect();
    //Initial values
    var initWidth = 34.0;
    var initHeight = 24.0;

    //Crazy calculations for the physics of the game
    var boxWidth = initWidth - (Math.sin(Math.abs(rotation) / 90) * 8);
    var boxHeight = (initHeight + box.height) / 2;
    var boxTop = ((box.height - boxHeight) / 2) + box.top;
    var boxLeft = ((box.width - boxWidth) / 2) + box.left;
    var boxRight = boxLeft + boxWidth;
    var boxBottom = boxTop + boxHeight;

    //Checks if the player collided with the ground
    if(box.bottom >= $("#land").offset().top){
        playerDead();
        return;
    }
    
    //Checks if the player collided with the ceiling
    else if(boxTop <= ($("#ceiling").offset().top + $("#ceiling").height())){ 
        position = 0;
    }
    
    //Checks if there is no obstacle in game
    else if(obstacle[0] == null){ 
        return; 
    }

    //Determines the area for the next obstacles
    var nextObstacle = obstacle[0];
    var nextObstacleUpper = nextObstacle.children(".obstacle_upper");   
    //More crazy calculations for the physics of the game
    var obstacleTop = nextObstacleUpper.offset().top + nextObstacleUpper.height();

    //For some reason it starts in the displacement of inner tubes, not the outer tubes
    var obstacleLeft = nextObstacleUpper.offset().left -2;

    var obstacleRight = obstacleLeft + obstacleWidth;
    var obstacleBottom = obstacleTop + obstacleHeight;

    if(boxRight > obstacleLeft){
        if((boxTop > obstacleTop) && (boxBottom < obstacleBottom)){

            //Optional code...

        }else{
            playerDead();
            return;
        }
    }
    
    //Verifies that the player has passed over the obstacle
    if(boxLeft > obstacleRight){
        // Next obstacle
        obstacle.splice(0, 1);
        updateScore();
    }

}
```


## To contributions 

Please, see [doc for contribute](https://github.com/lleocastro/styles-guide/blob/master/CONTRIBUTE.md). Thanks!


### License

That Style guide is licensed under the MIT license. See [License File](https://github.com/lleocastro/styles-guide/blob/master/LICENSE) for more information.
