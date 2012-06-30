# Fast, Not Furious: Performance Tuning that Works

Davey Shafik

[http://joind.in/talk/view/6349](http://joind.in/talk/view/6349)

[@dshafik](http://twitter.com/dshafik)

[davey@engineyard.com](mailto:davey@engineyard.com]

[daveyshafik.com/slides](http://daveyshafik.com/slides)
- Orchestra.io
- EngineYard

"Hardware is cheap, programmers are expensive." — Jeff Atwood

"But only if you respect the hardware." — Davey Shafik

- Anecdote
	- story about a process requiring 15 minutes and consuming 8GB of RAM
	- random optimizations can be problematic
	- make one change at a time, so taht you know what each change does
- Common Causes of Slowdowns
	- databases
	- external resources (processes, APIs, etc.)
	- code
	- "The only great code is code that never has to run."
- Do You Have a Problem?
	- identify your expected performance so that you can evaluate whether there is a problem at all
	- benchmark your performance on an environment comparable to your production environment
		- testing on a MacBook Air is unrealistic if your production is a giant VPS
	- Profiling and Benchmarking
		- profiling affects speed
		- relative measures available through profiling
		- benchmarking measures absolute performance
- Profiling with xhprof
	- profiling tool by Facebook
	- Installing xhprof
		- install from source (./configure && make && make install)
		- update php.ini
		- restart web server
	- Installing xh-gui
		- clone from github (preinheimer/xhprof)
		- configure database adapater
	- add xh-gui config to xhprof
	- Using xhprof/xh-gui
		- add prepend/append config to php.ini
			- auto_prepend_file = '/xhprof/header'
			- auto_append_file = '/xhprof/footer'
		- demo of xh-gui
		- demo of xhprof
			- there are vaious options for profiling and benchmarking; understand the performanc implications of system overhead
			- cast information in APC to maximize performance
- General Guidelines
	- make no assumptions
	- make small changes
	- test
- Caching
	- Key-Value Stores
		- APC (not particularly good for multi-server systems)
		- Memcache
		- Redis
		- etc.
	- Memcache
		- originally created by Livejournal, in Perl
		- simple clustering integrated
		- entire cache destroyed at once
		- Namespaces
			- use a key containing a number for the version of the cache to access
			- create a namespace key in memcache
				- memcache_set('mynamespace', rand(1,1000 ));
			- use the namespace name, value, and items in unique key to create key
				- namespace_189_a93849223498239742...
			- when you want to clear the cache, increment the namespace key
				- memcache_increment('mynamespace');
		- Namespace Segmenting
			- create a segment key
				- memcache_set('namespace_config', rand(1, 000));
			- use namespace name, value, segment name, value, and unique key to create key
				- example.org_session
				- example.org_public
				- example.org_admin
				- example.org_config
				- …
		- code example
			- require_once 'Cache/Memcache.php';
			- $cache = new Cache_Memcache();
			- $cache->get($url, 'namespace') may get cached output, is false otherwise
			- $cache->set($url, $data, 'namespace');
			- $cache->clearCache()
		- Other Memcache Tricks
			- use a meta-key to store additional information about a cached item
			- split up large items in 1MB chunks in order to use Memcache for larger items
		- additional code example
			- custom function for getting a Memcache key
			- custom _set_ function for putting data into Memcache
				- split items into 1MB slabs
				- add meta entries indicating lastModified and # slabs
			- custom _get_ function for retrieving data from Memcache
				- assume single-slab item in absence of meta entry
			- example of putting an image into Memcache
- Getting Inside PHP
	- Opcodes
		- intermediate instructions into which PHP is converted
		- the Zend Engine runs the opcodes
		- PHP vs. Java
			- PHP
				- parse
				- compile to opcodes
				- execute
				- output
			- Java
				- parse
				- convert to bytecode
				- save as binary
				- …
			- PHP with APC
				- check opcode cache
				- not cached
					- go through caching process
				- cached
					- read from shared memory

[http://joind.in/talk/view/6349](http://joind.in/talk/view/6349)

[@dshafik](http://twitter.com/dshafik)

[davey@engineyard.com](mailto:davey@engineyard.com]

[daveyshafik.com/slides](http://daveyshafik.com/slides)
