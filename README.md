# jfPopUp
jQuery plugin designed to load html popup messages. 


## Script Set Up
Just follow these steps to enable:

1. Include jQuery on your page.

    ```html
    <script src="http://code.jquery.com/jquery.min.js"></script>
    ```

2. Download and include jfPopUp after jQuery and before its first use.

    ```html
    <script src="jquery.jfPopUp.js"></script>
    ```
3. Download and include jfPopUp.css in the head of the html.

    ```html
    <link href="css/jfPopUp.css" rel="stylesheet" type="text/css" />
    ```

4. Init the plugin by attaching it the elements you want responsible for launching external files.
    ```js
    $(window).jfPopUp({auto:true, message:'type your message here'});
    ```
    
## Demo
https://codepen.io/fonstok/pen/yPQLQx

## Options and Defaults
__Options__ and *Defaults*

#### Basics
* __loadElement:__ *'body'* The element you want the light box to be loaded into.
* __message:__ *'type your message here'*  The message you want the popup to display.
* __auto:__ *false*  Launch message on page load.
* __mouseEvent:__ *'none'*  You can pass it a mouse event on the object to trigger launch.

#### Window Animation
The window fades in by default, but you can pass it From and To properties via lists and CSS properties to change its animation. The out will be the reverse of what ever you set.
* __animationFrom:__ *{opacity:'0', 'margin-top':'100px'}*  The load window's animation starting properties.
* __animationTo:__ *{opacity:'1', 'margin-top':'0px'}*  The load window's animation ending properties.
* __pause:__ *0*  Pause time before the window comes in.
* __speed:__ *100*  Speed of window animation.
* __ease:__ *'swing'*  You can pass the animation an ease, __but you must to link to a library or plugin such as, jqueryUI, that includes ease options__.

#### Passing Functions
* __onStart:__  You can pass a function to be called when the load has started.
* __onStartArgs:__  If the onStart function has arguments, you can pass argument values via an array ['arg1', 'arg2'].
* __onComplete:__ You can pass a function to be called when the load is completed.
* __onCompleteArgs:__ If the onComplete function has arguments, you can pass argument values via an array ['arg1', 'arg2'].
* __onClosed:__  You can pass a function to be called when the window is closed.
* __onClosedArgs:__  If the onClose function has arguments, you can pass argument values via an array ['arg1', 'arg2'].

### Options as Arguments
Options can be passed as arguments through the init function.
```js
$('window').jfPopUp({
	message:'hello',
	auto:true,
	animationFrom:{opacity:'0', 'margin-top':'100px'},
	animationTo:{opacity:'1', 'margin-top':'0px'},
	pause:0,
	speed:100,
	ease:'swing',
	onStart:function(){console.log("started")},
	onComplete:function(){console.log("complete")},
	onClosed:function(){console.log("closed")},
  });
```
	
### Options as Data Attributes
Options can also be passed through data attributes in the opening of the attached element. __Note that the data attributes use dashes instead of camel case__.
```html
<div class="popupme" 
	data-message="Hello" 
>Mouse Over Me</div>
```

## Public functions
There are a few public functions that can be called at any time after init.
* __launch():__ This function can be called to launch the external file associated with the element it's attached to. It's handy for launching on a unique event like drag stop or drop. Additionally, you will most likely need to disable the click functionality by setting the __mouseEvent__ to "none".
* __close():__ This closes the window.
* __destroy():__ This deactivates the plugin.
* __init():__ This initates the plugin, this gets called automatically. 

```js
$(window).data("jfPopUp").launch();
$(window).data("jfPopUp").close();
$(window).data("jfPopUp").destroy();
$(window).data("jfPopUp").init();
```
## Structure
These are the elements the plugin creates.

```html
<div class="mb_messagebox">
	<div class="mb_shade"></div>
	<div class="mb_window">
		<div class="mb_content"><!--stuff gets loaded here --></div>
		<div class="mb_closeBtn">close</div>
	</div>
</div>
```

### Classes
* __.mb_messagebox__: The main parent element.
* __.mb_shade__: The backdrop area.
* __.mb_window__: The parent of the content area and close button. Gives you a layer to work with.
* __.mb_content__: Where the message be loaded.
* __.mb_closeBtn__: The close button.

## Credits
I used http://stefangabos.ro/jquery/jquery-plugin-boilerplate-revisited/ as a starting point for the plugin.


