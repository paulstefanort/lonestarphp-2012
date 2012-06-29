# Building Testable PHP Applications
Chris Hartjes
Lone Star PHP - June 29, 2012
[@grmpyprogrammer](http://twitter.com/grmpyprogrammer)

- Story Time
	- started using PHP in 1998
	- discovered testing in 2004(?)
	- strongly familiar with testing
	- struggling with architectural constraints in an application
	- began using SimpleTest
- Why do we test?
	- Because programming is hard.
	- increasing complexity is necessitating testing
	- testing is not only to make sure that your code works, but also to make sure that you do not break things when making changes
- A Huge Topic
	- much could be said about testing
	- entire seminars could be devoted to testing
- Uncomfortable Truths
	- some of this will not make sense to you (?)
	- sometimes applications are structured in such a way that unit testing is infeasible
	- testing is good
	- testable actions are better
	- like losing weight (or some other challenge), PHP testing requires time and dedication
	- the barrier to entry for PHP is extremely low; discipline and determination are required for the embracing of a greater level of quality
- It’s About Tools
	- make the application itself more testable
	- code, review, integration
	- PHPUnit, Selenium, etc.
- It’s About Strategies
	- tools are not enough
	- it is insufficient to simply have a testing framework; ensure that code is testable
- Automation is Key
	- effective application testing requires an automation of the process
	- write code, save file, refresh the browser - ghetto testing, unsustainable, not scalable, not repeatable
	- manual testing fosters the use of foolish shortcuts
	- automated testing can ensure that errors are minimized
	- "Write a script that will run all your tests before you go live."
	- "The job of the test is to tell you that something is wrong before your users tell you."
	- configure version control to run all tests when you commit or push (hooks)
	- continuous integration
		- [Jenkins](http://jenkins-ci.org)
		- [Travis CI](http://travis-ci.org)
- Architecture
	- "Simple systems can display complex behavior but complex systems can only display simple behavior."
	- large, legacy, procedural systems are difficult to test
	- "Build a large application as a bunch of small ones."
	- "Inside every great large application are many great small applications."
	- "Your framework is a deail, not the core of your application." -- Bob Martin (_Architecture: The Lost Years_ @ Ruby Midwest)
- Law of Demeter
	- Pragmatic Progammer
- Dependency Injection
	- constructor (pass dependencies in the constructor)
	- setter (inject dependencies after the object has been created)
	- (minimize coupling)
	- "Your objects should only know how to use the dependencies, not how to create them."
- Mock Objects
	- "Mock objects allow you to test code in proper isolation."
	- unit testing: do not touch database
	- integration testing: make modifications to the database
	- common mock objects
		- database connections
		- web services
		- file system operations
			- BFS Stream ("write" files to memory instead of to the file system)
- How do we test this?
	- "Protected and private methods and attributes are difficult to test properly."
	- application architecture determines testability
- Methods?
	- [Etsy's PHPUnit Extensions](https://github.com/etsy/phpunit-extensions)
		- uses annotations to flag methods you wish to test (annotations around protected methods)
		- incorporates PHP’s Reflection API to turn protected methods into public methods for test purposes
	- (http://www.gpub.ca/2012/06/02/testing-protected-methods-with-phpunit)http://www.gpub.ca/2012/06/02/testing-protected-methods-with-phpunit
		- new ReflectionMethod
		- setAccessible(true)
		- assert results of function call
	- PHPUnit allows atttribute values to be checked, but cannot set them
	- "If your unit test actually uses the database, you are doing it wrong."
	- use mocks instead of fixtures
	- PHPUnit_Framework_Testcase -> getMockBuilder 
	- PHPUnit Testing Cookbook (in progress)
	- "API calls should be done via wrapper methods."
- Environments
	- "Your app shouldn’t care what environment it runs in."
	"Keep config files for each environment under version control."
	- [https://github.com/flogic/whiskey_disk](https://github.com/flogic/whiskey_disk)
- Resources
	- [PHPUnit](http://phpunit.de)
	- [Behat](http://behat.org)
	- the people sitting next to you (value of collaboration)
	- [The Grumpy Programmer’s Guide to Building Testable PHP Applications](http://grumpy-testing.com)

[@grmpyprogrammer](http://twitter.com/grmpyprogammer)
[http://www.littleheart.net/atthekeyboard](http://www.littleheart.net/atthekeyboard)
[http://joind.in/6335](http://joind.in/6335)
