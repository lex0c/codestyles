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

###### This example of codification is following the my codestyles. This code is of my project '[encryptor](https://github.com/lleocastro/encryptor)'.
```php
<?php namespace Encryptor\Suite;

/*
 ===========================================================================
 = Hash Generator
 ===========================================================================
 =
 = Generates a 107 bits hash for encoding passwords and data that does not 
 = need to retrieve the value retrieved.
 = 
 */

use \Encryptor\Suite\Disguise;
use \InvalidArgumentException;

/**
 * PHP Hard Hash Generator
 * Safety against scripts injections
 * Generates an encrypted hash of 107 byte
 * @link https://github.com/lleocastro/encryptor
 * @license https://github.com/lleocastro/encryptor/blob/master/LICENSE
 * @author Leonardo Carvalho <leonardo_carvalho@outlook.com>
 * @copyright 2016 MIT License
 * @package \Encryptor
 */
class HashGenerator extends Disguise
{
    /**
     * Encryption prefix
     * @see http://www.php.net/security/crypt_blowfish.php
     * @var string
     */
    protected $prefix = '2a';

    /**
     * Salt [MTc2MzMxNDQ4NTdmZDg4Yz]
     * @see http://www.php.net/security/crypt_blowfish.php
     * @var string
     */
    private $salt = '';

    /**
     * Custo default '8' [4 <> 31]
     * @see http://www.php.net/security/crypt_blowfish.php
     * @var int
     */
    protected $cust = 8;

    /**
     * Secret hash for hard encryption
     * @var string
     */
    private $secret = [];
    private $key = '';


    /**
     * Encrypter Factory
     * @param string $prefix
     * @param string $salt
     * @param int $cust
     */
    public function __construct(string $prefix = '', string $salt = '', int $cust = 8)
    {
        if(($cust < 4) || ($cust > 31)):
            throw new InvalidArgumentException('Arguments not valid!');
        endif;

    	$prefix = trim(htmlentities(strip_tags($prefix)));
    	$salt   = trim(htmlentities(strip_tags($salt)));
    	$cust   = htmlentities(strip_tags($cust));
    	
        $this->prefix = ((empty($p))?'2a':$prefix);
    	$this->salt   = ((empty($s))?$this->generateHash():$salt);
        $this->cust   = ((empty($c))?8:$cust);
    }

    /**
     * Encrypt Generate
     * @param string $value
     * @return string encrypted
     */
    public function encode(string $value):string
    {
        return str_replace('=', '', strrev($this->obscure(
            crypt(
        	    (string) trim(htmlentities(strrev($value))), 
        	    $this->generateHash()
            )
        )));
    }

    /**
     * Compare hashes
     * @param string $value
     * @param string $hash
     * @return boolean
     */
    public function isEquals(string $value, string $hash):bool
    {
	    $v = (string) trim(htmlentities(strrev($value)));
	    $h = $this->illumin((string) trim(htmlentities(strrev($hash))));
        
        if(crypt($v, $h) === $h):
            return true;
        endif;

        return false;
    }

    /**
     * Generate a random salt
     * @return aleatory string encoded
     */
	protected function generateSalt():string
	{
        return substr(base64_encode(uniqid(mt_rand(), true)), 0, 22);
	}

    /**
     * Build a hash string for crypt
     * @return formated string
     */
	protected function generateHash():string
	{
        return sprintf('$%s$%02d$%s$', $this->prefix, $this->cust, $this->generateSalt());
	}

}
```

- [HTML Code Style]()

###### This example of codification is following the my codestyles. This code is of my project '[flappy-bird](https://github.com/lleocastro/flappy-bird)'
```html
<!DOCTYPE html>
<html lang="pt-br">   
<head>
    <meta charset="utf-8">
    <meta name="description" content="Divirtam-se com esse jogo viciante e desafiador."/>
    <meta name="author" content="lleocastro"/>
    <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
    <meta name="robots" content="index, follow"/>

    <link rel="icon" type="image/png" href="assets/icon.png"/>
    <link rel="stylesheet" href="css/reset.css"/>
    <link rel="stylesheet" href="css/style.min.css"/>

    <title>Flappy Bird</title>
</head>
<body>
<!-- This code is old, so disregard the excessive use of 'ids', most 'ids' are used in JS -->
<main id="background-pag" style="background-image: url('assets/background_pag.jpg');">
    <div id="modal">
        <section id="game-area">          
            <section id="background-game" class="animated">
                <section id="flight-area">
                    <div id="ceiling" class="animated"></div>
                    <div id="player" class="personage animated"></div>  
                    <div id="score"></div>
                    <div id="splash-screen"></div>
                    <div id="scoreboard">
                        <div id="medal"></div>
                        <div id="current-score"></div>
                        <div id="best-score"></div>
                        <div id="restart"><img src="assets/scenery/restart.png" alt="restart game"></div>
                    </div>
                    <!-- The obstacles will appear here by means of an array -->
                </section>
            </section>            
            <footer id="land" class="animated"></footer>
        </section>
    </div>
</main>
</body>
    <!-- APIs and game logic -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/2.2.4/jquery.min.js"></script>
    <script src="js/libs/jquery.transit.min.js"></script>
    <script src="js/libs/buzz.min.js"></script>
    <script src="js/logic.min.js"></script>
    <script>
        alert('Controllers: Mouse click or space key');
    </script>
</html>
```

- [CSS Code Style]()

###### This example of codification is following the my codestyles. This code is of my project '[bootstyle](https://github.com/lleocastro/bootstylle)'.
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

###### This example of codification is following the my codestyles. This code is of my project '[flappy-bird](https://github.com/lleocastro/flappy-bird)'.
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
