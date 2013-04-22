Javascript Modification Proposal
================================

Members: Justin Powell, James Ontiveros, Tom Spooner

Overview:
---------
When looking at javascript and what it has to offer, some may wonder what would make it easier and more efficient. One answer would be to add modules into the language and simplify them for easy and intuitive use. Modules would allow reuse of advantageous code throughout a project.

Modules are similar to objects, but must be explicitly exported to be made visible externally. Modules can either be defined as inline or as external files which allow the use of blocks of code which can be utilized throughout the project. This is very useful if one is looking for an external widget that they want to incorporate into their project. 

```javascript
	module Car{
		// import code
		// export code
	}
```

This simple example shows what a module can do.

Module *instances* are modules which have been evaluated, linked to other modules, or holds lexically encapsulated data. Here is an example of a module instance:
	
```javascript
	module myCar at "car.js"
```

You can also declare modules in the following way:

```javascript
	module UniverseTest {};
	module Universe { module MilkyWay {} };
	module MilkyWay = 'Universe/MilkyWay';
	module SolarSystem = Universe.MilkyWay.SolarSystem;
	module MySystem = SolarSystem;
```

Exporting and Importing:
------------------------
Any `export` declaration make functions and variables visible to other modules. This obviously makes modules very useful when creating a project. It's similar to a class in Java or C++ with public and private variables. The programmer can choose what to export from his/her module which is a powerful tool. Here is an example of some exporting:

```javascript
	module Car {
	  	// Internal
	  	var licensePlateNo = '556-343';
	  	// External
	  	export function drive(speed, direction) {
	    	console.log('details:', speed, direction);
	  	}
	  	export module engine{
	  	  export function check() { }
	  	}
	  	export var miles = 5000;
	  	export var color = 'silver';
	};
```
A programmer can `import` variables and other functions from another module that he/she wants to utilize. This can be seen above with the `export` declaration in the `Car` module. A programmer may import the function `drive()` or `check()`, or he/she can import the variables `miles` or `color`. Even though a programmer can import these functions or variables, he/she cannot redefine them. (Exports can be renamed to distinguish them from other local variables)

A programmer may also choose what they want to import from certain modules so that they don't need to import the entire thing. This is very useful if the programmer only wants one function or variable from a module. Even with a few variables or functions it would be smart to not import the entire module if one will not utilize all of its content.

Import `drive()` from car.

```javascript
		import drive from Car;
```

Import `drive()` and `miles` from car.

```javascript
		import {drive, miles} from Car;
```

Modules are very diverse in what they allow us to do. We can `import` what we need or `export` functions that will come in handy later. They are useful blocks of code that are easily accessed with a single line of code. This makes writing concise code easier and quicker than before. A programmer can have his/her modules be the backbone of a project, they can then import everything needed from his/her modules and their project will be underway. Open source modules will also help other developers with their projects if they can't be bothered to write their own. `Importing` and `exporting` modules will save a lot of time in the long run.

Module Loader API:
------------------
ES.next states that it aims to develop a "dynamic, reflective API for loading module scripts in controlled and selective contexts." Each host environment comes with a built-in system where users can create custom loaders using the Loader constructor. Some of the goals listed by ES.next in providing this loading functionality includes providing dynamic loading, nested virtualization and state isolation. 

The functionality is similar to that of import, in that it can consume anything defined as an export from a seperate module, like below:
```javascript
	// Signature: load(moduleURL, callback, errorCallback)
	Loader.load('car.js', function(car) {
  	  console.log(car.drive(500, 'north'));
	}, function(err) {
  	  console.log('Error:' + err);
	});
```
And another:
```javascript
Loader.load('http://json.org/modules/json2.js',
    function(JSON) {
        alert(JSON.stringify([0, {a: true}]));
    });
```

load() has 3 arguements, being:

* moduleURL: The address of a module to taken in, in the case above, this is car.js
* callback: A callback function which receives the output result of attempting to load, comple and then execute the moduke
* errorCallback: A callback triggered if an error occurs during compilation


Classes:
--------
The changes being made in ES.next to add class functionality are to simplify the readabilty of the code, in which code becomes easier and faster to write. Below is an example comparing code written for ES.next, compared to code written for modern day javascript:

```javascript
   module widgets {
  	// ...
 
     export class DropDownButton extends Widget {
       constructor(attributes) {
      	    super(attributes);
      	    this.buildUI();
       }
 
       buildUI() {
         this.domNode.onclick = (e) -> {
        	// ...
       	 };
       }
    }
  }
```

And in today's javascript:

```javascript
var widgets = (function(global) {
  // ...
 
  function DropDownButton(attributes) {
    Widget.call(this, attributes);
    this.buildUI();
  }
 
  DropDownButton.prototype = Object.create(Widget.prototype, {
    constructor: { value: DropDownButton },
    buildUI:     {
      value: function(e) {
        this.domNode.onclick = function(e) {
          // ...
        }
      }
    }
  });
})(this);
```

As we can see, classes are syntactic sugar for function in the current release of javascript. The benefit of class functionality is to reduce complexity of code, and make it easier to read.

The Proposal:
-------------
<<<<<<< HEAD
Overall, the goals set forth in module functionality in ES.next include providing faster compilation, easy external loading, and above all increasing simplicity and usability. 
This reasoning in itself, provides the justification for including modules in the the development of javascript.
Well written modules have the advantage of making code more scalable. That is, when designed well, modules can work independently of each other, and can be added or removed efficiently. This has the benefit of making collaboration much easier, as developers can be assigned with the task of designing certain modules independent of one another, and only have to worry about minimal conflicts. Coding styles or preferences can be utilized by the individual, and there is no conflict when they are brought together, hindering the coding process.

=======
Overall, the goals set forth in module functionality in ES.next which includes providing faster compilation, easy external loading, and above all increasing simplicity and usablility. 
This reasoning in itself, provides the justification for including modules in the the development of javascript....
>>>>>>> fa4268d916301edc563cd2526556e51fc3a21bd8

> Sources that will be used are: [strawman:simple_module_functions](http://wiki.ecmascript.org/doku.php?id=strawman:simple_module_functions) and [blogs  that we find](http://addyosmani.com/blog/a-few-new-things-coming-to-javascript/)
