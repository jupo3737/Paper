##Addition of Module Functionality to ES.next/Javascript

CSCI 3155 - Lightning Talk

Thomas Spooner, Justin Powell, James Ontiveros

##Overview:

* Currently, Javascript doesn't have an easy way to reuse code throughout a project
* Modules would allow such reuse to happen in an easy way
* Modules will make javascript more scalable in a sense of new features and easy implementation

##Details of Development
* Modules have been approved for ES.next
* Good News!!!

##History
* Modules have been in javascript, but they weren't easy to use

##How it looked before

```javascript
  var MODULE = (function (my) {
  // add capabilities...

  return my;
  }(MODULE || {}));
```

##What are modules
* Modules are blocks of code that can be reused throughout a project
* They allow a programmer to choose which variables or functions to import or export
* They make code look clean and concise

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

##Import Example
```javascript
  import Car;
  import drive from Car;
  import {drive, miles} from Car;
```

##Exporting Code
* Txporting lets the programmer choose which blocks of code can be accessed by the porgram
* Declarations declare that a local binding at the top-level of the module is visible externally to the module
* Other modules can read the module exports but cannot modify or reset them

##Exporting Example

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
##Module Loader - Tom will fill this
* Es.next aims to develop a "dynamic, reflexive API for loading module scripts
* Functionality similar to import as shown below

```javascript
  Loader.load('car.js', function(car) {
    console.log(car.drive(500, 'north'));
  }, function(err) {
  console.log('Error:' + err);
  });
```

##Proposal
* Implement modules into javascript
* They will help make javascript easier to use and cleaner
* Clean up how we declare modules

##Conclusion
* Modules are awesome and should be put into javascript
* They help outside of web development
