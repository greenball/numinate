### Greenball Numinate jQuery plugin, to animate the world <3
***
jQuery plugin made to animate numbers while counting them up or down.

[Github Page](http://greenball.github.io/numinate/), 
[Live demos](http://greenball.github.io/numinate/demos.html)

### So, what's this for? Where to use?
***
+ Animate progress stages.
+ Display loading time for ajax requests.
+ Display elapsed time.
+ Countdown untill x event.
+ Make showout :P

### How to use
***
You can download and see the demos.html to see in action, but here is some resolutin:

```js
// Count the elapsed time.
$('#target').numinate({format: 'Page has been loaded %counter% seconds ago.', stepUnit: 0.1, stepInterval: 100, precision: 1});

// Update the progress stage.
$('#progress').numinate({format: '%counter%\% has been loaded...', stepUnit: 1, from: 5, to: 42, runningInterval: 1500});

// Countdown for bombs <3
$('#bomb-defuser-kit').numinate({
	format: 'Bomb will explode in %counter% seconds!!', 
	from: 10,
	to: 0, 
	runningInterval: 10000, 
	stepUnit: 0.1, 
	autoStart: false, 
	onStop: function(element, options, current) {
		element.text('We are in safe! Just made it '+current+' before the bum!');
	},
	onComplete: function(element, options, current) {
		element.text('Kabuum!!!');
	},
});

// You can operate with the counter as:
$('#bomb-defuser-kit').numinate('start');
$('#bomb-defuser-kit').numinate('step');
$('#bomb-defuser-kit').numinate('stop');
$('#bomb-defuser-kit').numinate('restart');
$('#bomb-defuser-kit').numinate('remove');
```

### Hooks & Callbacks
*** 
The plugin will fire every possible event what you can imagine... 

+ onCreate() Event called when the counter has been created.
+ onStart() Event called when the counter starts to count.
+ onStep() Event called before the counter up the step value.
+ onStop() Event called when the counter reached the goal, or stoped manualy.
+ onComplet() Event called when the counter reached the goal value, or called manualy.
+ onRemove() Event called when the counter has been removed.

To listen events simply add the callback in the initialization config.

```js
// Will be called before the new value is rendered.
$('#ticker').numinate({onStep: myCallback, stepUnit: 1, stepInterval: 1000 });
```

### Calculation conditions
***
Here is some variable and logic what you need to follow.

+ Either runningInterval or stepInterval need to be provided.
+ If both stepUnit and stepCount setted then the 'to' value will be overwriten.
+ Either stepUnit or stepCount is need to be provided.
+ If stepInterval is less then 10 ms then the plugin will recalculate the animation with 10 ms stepInterval.
+ If the 'from' and 'to' values are both zer0 the plugin will count infinity if no runningInterval provided or will count till reaches the runningInterval's end.

### Install
***
The plugin to work with AMD structure. Further documentation is required.

### Licence
***
The source code is published under the MIT license, do what ever you want with it <3

### Origin
***
I needed to animate HP lose for an online game, this was in 2011... first I wrote an jQuery UI widget for it which you can still download @ [Greenball/counterWidget](https://github.com/greenball/counterWidget) repo. This plugin is made at 2013's end where I needed to count the elapsing seconds (more like fractions but nah) while loading an ajax content but at this time I rewrote to use without the jQuery UI and also removed some unecessary methods, after that I was thinking to make it into an AMD plugin and this is the current history of this code snippet. If you read all of those, then something clearly wrong with you.. (said by some1 who was nuts enough to write it :O)
