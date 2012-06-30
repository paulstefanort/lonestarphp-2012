# Micro Frameworks and JavaScript Applications

Jeff Carouth

[github.com/jcarouth/pomtrac](http://gitub.com/jcarouth/pomtrac)

[joind.in/6351](http://joind.in/6351)

[@jcarouth](http://twitter.com/jcarouth] (also on GitHub: [@jcarouth](http://github.com/jcarouth))

[jcarouth@gmail.com](mailto:jcarouth@gmail.com)

carouth.com

Web & Mobile, Agile Apprentice

- The MicroPHP Manifesto
	- originally by @funkatron
	- Composer
	- Slim
	- Backbone.js
- Learning a comprehensive framework is hard.
- PHP is complicated enough.
	- maintenance troubles of significant library use
- PHP’s roots
	- simple way to add dynamic elements to a website
	- Personal Homepage Tools
	- 1998: hypertext preprocessor
	- community contributions (modules, extensions)
- Exposing MicroPHP
	- microphp.org
	- packagist.org (Composer)
	- "Composer is a tool for dependency management in PHP. It allows you to declrea the dependent libraries your project needs and it will install them in your project for you." -- The FM
- Slim: micro framework
	- (micro frameworks primarily provide routing capabilities)
	- receive requests, send responses
	- useful for wrapping an existing application, exposing data via an API
	- REST
		- GET, POST, PUT, DELETE
	- PomTrac
		- tasks API
			- GET /tasks
				- return the collection of tasks stored in the system
			- POST /tasks
				- create a new task, inserting it into the collection
				- return location
			- GET /tasks/<id>
				- return the task with the specified _id_
				- return 404 if the item does not exist
			- PUT /tasks/<id>
				- update the task with the specified _id_
				- return a 200 if update successful, otherwise return 500
			- DELETE /tasks/<id>
				- remove the task with the specified _id_
				- return a 204 if delete successful, otherwise return 500
		- Backbone.js
			- structure with models, collections, and views
			- simple binding and handling of events
			- connection to RESTful JSON API
			- lightweight JavaScript "MVC"
				- Backbone.Model
				- BackBone.Collection
				- View
					- view "controller"
					- templates, underscore.js
				- Backbone.Events
				- Implementation
					- retrieve data from API
						- App.Task = Backbone.Model.extend({});
						- urlRoot = 'tasks', defaults: function() {}
						- App.Tasks = Backbone.Collection.extend({ model: App.Task, url: '/tasks', comparator: function(task) {}  })
						- var tasks = App.Tasks();
						- tasks.fetch(); // calls API and returns App.Task models in the App.Tasks collection
					- render HTML
						- App.TaskView = Backbone.View.extend({});
						- tagName = 'dif', className: 'inventory-row', template: _.template($('#pomtrac-task-tmpl').html())
						- initialize: function() {}, render: function() {}
						- <script type="text/javascript" id="pomtrac-task-tmpl">…</script>
						- App.ActivityInventoryView = Backbone.View.extend({initialize: function(){}, render: function(){}, renderTask: function(){}})
					- handle events
						- change, click, hover, dblclick, etc.
						- App.TaskView = BackBone.View.extend({ events: { 'change .textinput': 'update', update: function() {} } })
					- configure application
						- App namespace
						- App.init = function() { $.ajaxSetup({'dataType': 'json'}); Backbone.emulateHTTP = true; ActivityInventory = new App.AcivityInventoryView({ el: $('#el') }) }
						- App.ready = function() { app.init() }
- Wrap Up
	- MicroPHP is about exposing small-footprint libraries that solve common problems.
	- Composer and Packagist help the PHP community by exposing micro frameworks and other libraries in an easy-to-consume manner.
	- Slim makes creating a RESTFUL API simple.
	- Backone.js provides just the structure a PHP dev like me needs to build on top of such APIs.

[github.com/jcarouth/pomtrac](http://gitub.com/jcarouth/pomtrac)

[joind.in/6351](http://joind.in/6351)

@jcarouth

[jcarouth@gmail.com](mailto:jcarouth@gmail.com)
