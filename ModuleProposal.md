Javascript Modification Proposal
================================

Members: Justin Powell, James Ontiveros, Tom Spooner

Overview:
---------
When looking at javascript and what it has to offer, some may wonder what would make it easier. One answer to that question is to add modules into the language and simplify them for easy use. Modules would allow reuse of advantageous code throughout a project.

Modules can either be defined as inline or as external files which allow for use of blocks of code that will be utilized throughout the project. This is very useful if one is looking for an external widget that they want to incorporate into their project. 

	module Car{
		// import code
		// export code
	}

This simple example shows what a module can do.

Module *instances* are modules which have been evaluated, linked to other modules, or holds lexically encapsulated data. Here is an example of a module instance:

	module myCar at "car.js"

You can also declare modules in the following way:

	module UniverseTest {};
	module Universe { module MilkyWay {} };
	module MilkyWay = 'Universe/MilkyWay';
	module SolarSystem = Universe.MilkyWay.SolarSystem;
	module MySystem = SolarSystem;


Modules in Depth:
-----------------


The Proposal:
-------------




> Sources that will be used are: [strawman:simple_module_functions](http://wiki.ecmascript.org/doku.php?id=strawman:simple_module_functions) and [blogs  that we find](http://addyosmani.com/blog/a-few-new-things-coming-to-javascript/)
