Javascript Modification Proposal
================================

Members: Justin Powell, James Ontiveros, Tom Spooner

Overview:
---------
When looking at javascript and what it has to offer, some may wonder what would make it easier. One answer to that question is to add modules into the language and simplify them for easy use. Modules would allow reuse of advantageous code throughout a project.

Modules can either be defined as inline or as external files which allow for use of blocks of code that will be utilized throughout the project. This is very useful if one is looking for an external widget that they want to incorporate into their project. 

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
Any `export` declaration make functions and variables visible to other modules. This obviously makes modules very useful when creating a project. It's basically like a class in Java or C++ with public and private variables. The programmer can choose what to export from his/her module which is a powerful tool. Here is an example of some exporting:

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

A programmer may also choose what they want to import from certain modules so that they don't need to import the entire thing. This is very useful if the programmer only wants one or function or variable from a module. Even with a few variables or functions it would be smart to not import the entire module if one will not utilize all of its content.

Import `drive()` from car.

```javascript
		import drive from Car;
```

Import `drive()` and `miles` from car.

```javascript
		import {drive, miles} from Car;
```

Modules are very diverse in what they allow us to do. We can `import` what we need or `export` functions that will come in handy later. They are useful blocks of code that are accessed with a single line of code. This makes writing concise code easier and quicker. A programmer can have his/her modules be the backbone of a project, he/she can then import everything that he/she needs from his/her modules and his/her project will be underway. Open source modules will also help other developers with their projects if they can't be bothered to write their own. `Importing` and `exporting` modules will save a lot of time in the long run.


The Proposal:
-------------




> Sources that will be used are: [strawman:simple_module_functions](http://wiki.ecmascript.org/doku.php?id=strawman:simple_module_functions) and [blogs  that we find](http://addyosmani.com/blog/a-few-new-things-coming-to-javascript/)
