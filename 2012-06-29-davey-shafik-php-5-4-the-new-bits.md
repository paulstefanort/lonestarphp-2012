# PHP 5.4: The New Bits

Davey Shafik

[@dshafik](http://twitter.com/dshafik)

[davey@engineyard.com](mailto:dave@engineyard.com)

- About These Slides
	- not simply showing what the speaker is saying
- The Small Stuff
	- new session handler interface that can be passed to session_set_save_handler
	- something I missed
	- new notice thrown for array/string comparison
	- improved memory usage and performance
	- similar performance increase between 5.4 and 5.3 as between 5.3 and 5.2
	- UTF-8 by default instead of Latin-1
- Language Changes
	- short echo tags no longer depend on _short_open_tags_ (will always work!)
	- binary numbers (in addition to integer, signed integer, float, octal, etc.)
	- new array syntax
		- same as JavaScript
		- array(...), []
	- array dereferencing
		- $foo = returnArray()['a']
	- dynamic method calls
		- variable static methods - ClassName::{$var}();
		- instantiation time access - (new ClassName)->instanceModel(); // loses the object
		- possible to combine - (new ClassName)::{$var}();
	- improvements to closures and callbacks
		- callable return type (in addition to function and string) (?)
		- reference $this from a closure (early binding)
		- $variable() for function calls within a closure
		- Callable Type hint
			- function (callable $var) {}
		- $this in closures
			- returns null in PHP 5.3 (returns $this within the context of the object containing the closure in 5.4)
		- array callbacks
			- $callBack = ['class', 'method'];
			- $callBack()
		- rebinding $this
			- break the object model
			- object to which $this points, scope of $this
			- change scope independently of the object
			- does not change the original closure, returns a clone
			- $closure = $objectA->getClosure(); $closure->bindTo($objectB);
			- Closure::bind($closure, $object);
			- $closure->bindTo($objectID, $scopeObjectID);
	- Traits
		- AKA horizontal re-use
		- "compiler-level copy and paste"
		- methods, abstract methods, properties available
		- trait myTrait { function myTraitFunction(){} }
		- trait mySecondTrait {}
		- class myClass { use myTrait,mySecondTrait }
		- $myClassObject->myTraitFunction();
		- inheritance/scope
			- extend a class that uses a trait
			- parent:: (called within a trait) references the parent of the class that uses the trait
		- precedence
			- use trait { functionName as public }
			- reassign scope, change name, change both
			- no inheritance with traits; they are "copied" at the "compiler level"
			- insteadof: {trait::function as functionName instead of function}...
		- trait detection
			- compiler phase (converting PHP to opcodes)
			- opcodes are stored in the cache (automatically)
		- built-in CLI server
		
[http://joind.in/talk/view/6336](http://joind.in/talk/view/6336)

[@dshafik](http://twitter.com/dshafik)

[davey@engineyard.com](mailto:dave@engineyard.com)

[http://daveyshafik.com/slides](http://daveshafik.com/slides)
