##Addition of Module Functionality to ES.next/Javascript

CSCI 3155 - Lightning Talk

Thomas Spooner, Justin Powell, James Ontiveros

##Overview:
* JavaScript - #11 on Tiobe list
* Currently, Javascript doesn't have an easy way to reuse code throughout a project
* Modules would allow such reuse to happen in an easy way
* Modules will make javascript more scalable in a sense of new features and easy implementation

##Details of Development
* Modules have been approved for ES.next
* Modules have been in development for a while to create a seamless implementation
* Good News!!!
 
##What are modules
* Modules are blocks of code that can be reused throughout a project
* They allow a programmer to choose which variables or functions to import or export
* They make code look clean and concise

##History
* Modules have been in javascript, but they weren't easy to use
* Introduced in Gecko 1.9 and used for sharing code between different scopes
* Modules were long, ugly and hard to follow at times

##How it looked before
* Previously implementable through "module pattern" - A common Javascript coding pattern
* Example module pattern with export capabilities:

```javascript
var MODULE = (function () {
	var my = {},
		privateVariable = 1;

	function privateMethod() {
		// ...
	}

	my.moduleProperty = 1;
	my.moduleMethod = function () {
		// ...
	};

	return my;
}());
```
This function returns my, the var to be exported. Now lets see what is proposed in es.next...

##Module Example
```javascript
  module Car{
  // import code here
  // export code here
  }
```
##Module Instances
* These are modules that have been evaluated, linked to other modules, or holds lexically encapsulated data
* These are basically objects that a programmer may use	
	
```javascript
  module myCar at "Car.js";
```

##Compared to other languages
* Python: `import fibo` (imports fibonacci function)
* Java: `import java.module.annotation.*;` (module in Java)
* Javascript: `????` (why???)
 
##Importing Code
* This lets programmers bring code into their project, either an entire module or just selected items from that module
* Bind another module's exports as local variables

##Import Example
```javascript
  import Car;
  import drive from Car;
  import {drive, miles} from Car;
```

##Exporting Code
* Exporting lets the programmer choose which blocks of code can be accessed by the program
* Declarations declare that a local binding at the top-level of the module is visible externally to the module
* Other modules can read the module exports but cannot modify or reset them

##Exporting Example
*Present day Javascript using modules:

```javascript
  module Car{
    // Internal
    var license-plate = "555-444";
    // External
      export var miles = 5000;
       export function drive(speed, direction){
       console.log('details: ', speed, direction);
	}
  }
```
##Comparison to Classes
* Modules basically have public and private variables, internal and external parts of the module
* Modules allow for the reuse of code throughout an entire project

##Example Classes: Before and proposed
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

```javascript  
module widgets {
  // ...
  class DropDownButton extends Widget {
    constructor(attributes) {
    super(attributes);
    this.buildUI();
    }
    buildUI() {
      this.domNode.onclick = function(){
      // ...
      };
    }
    }
}
```
##Module Loader API
* Es.next aims to develop a "dynamic, reflexive API for loading module scripts
* Functionality similar to import: Anything defined as an export can be consumed

```javascript
  Loader.load('car.js', function(car) {
    console.log(car.drive(500, 'north'));
  }, function(err) {
  console.log('Error:' + err);
  });
```
Custom loaders can be developed using the Loader constructor

##Proposal
* Implement modules into javascript
* They will help make javascript easier to use and cleaner
* Clean up how we declare modules

##Why does it matter
* Modules would make it easier to reuse code throughout a project
* Adds several benefits ranging from faster compilation to simplicity in external loading
* Portability between different host environments
* "Future-proof mechanism for platforms to introduce experimental libraries without collision" - harmony

##Conclusion
* Modules are awesome and should be put into javascript
* They help outside of web development
* Adds a standardized mechanism for creating libraries

##Works Cited

[Classes](http://infrequently.org/2012/04/class-warfare/)

[New Things Coming to Javascript - Modules](http://addyosmani.com/blog/a-few-new-things-coming-to-javascript/)

[Modules in the Past](https://developer.mozilla.org/en-US/docs/Mozilla/JavaScript_code_modules/Using)

[harmony:modules](http://wiki.ecmascript.org/doku.php?id=harmony:modules)

[Classes](http://infrequently.org/2011/09/why-class-doesnt-mean-what-you-think-it-means/)
