# SOLID - Not Just a State of Matter, It’s Principles for OO Propriety

Chris Weldon

[chris@chrisweldon.net](mailto:chris@chrisweldon.net)

[mojolive.com/profile/neraath](http://mojolive.com/profile/nerrath)

- Introduction
	- Texas Aggie
	- PHP Developer since 2003
	- Senior Consultant at Improving Enterprises
	- [apihackday.com](http://apihackday.com)
	- [chris@chrisweldon.net](mailto:chris@chrisweldon.net)

- What is OOD?
	- Abstraction
	- Inheritance
	- Encapsulation
	- Polymorphism
- Scenarios
	- New Requirements
		- fetch orders from database
		- fetch user for order
- SOLID
	- principles of object-oriented design
	- Single Responsiblity
		- "There should never be more than one reason for a class to change."
		- separate concerns into different classes
			- Order, OrderDao
			- OrderDeliverer, CustomerNotifier
		- (example of logging libraries)
			- Zend_Log
			- kLogger
			- log4php
			- log5php
			- pear/Log
	- Open/Closed
		- Open for Extension, Closed for Modification
		- extend classes, avoid overriding class properties
		- (example of DrillBitActivator)
			- specifying options in the constructor
			- avoid simply passing an array of options to a constructor
			- [defaults can be specified in constructors]
	- Interface Segregation
		- Having too many implementations in a single place minimizes usability and clarity
		- Arrange interfaces in such a way that all implementations are clear and reliably operational
		- better to have multiple interfaces than fewer but bloated ones
	- Liskov Substitution
		- "If your duck requires batteries, you need a different abstraction for it."
		- use polymorphism to minimize loading of multiple entities
	- Dependency Inversion Principle
		- "Would you solder a lamp directly to the elctrical outlet?"
		- "High-level modules should not depend upon low-level modules. They should depend upon abstractions." — Robert Martin
		- "Abstractions should not depend upon details. Details should depend upon abstractions." — Robert Martin
		- benefit: more flexibility
	- (review)
		- SOLID principles are useful
		- helpful guidelines for improving quality and maintainability
		- minimize the number of functions in an interface
- Dependency Injection
	- Involves a Service Container
		- configure chains of dependencies
		- allow all of the dependent objects for an object to be passed (you could control which ones to use in testing, for example)
		- sfServiceContainerSubclass example
		- "Just ask the service container for an item."
			- dependencies are abstracted away
			- request dependencies without caring about their location or implementation
	- Registers Chains of Dependencies
		- Code-Based Description
			- use a Builder (design pattern) to obtain layers/dependencies
		- Config-Based Description
			- XML or ini files
			- collections of parameters and arguments
	- Get the Object You Want
		- request dependencies from mechanisms that generate and provide them; avoid explicitly specifying dependencies
- Drawbacks
	- Can be confusing to junior developers
	- Potentially significant investment of time to understand the codebase (abstraction can increase conceptual complexity)

[joind.in/talk/view/6345](http://joind.in/talk/view/6345)
