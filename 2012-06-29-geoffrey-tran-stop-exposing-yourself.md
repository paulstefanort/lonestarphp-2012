# Stop Exposing Yourself: Exploits, Attacks and Defenses

Geoffrey Tran

[@geoffreytran](http://twitter.com/geoffreytran)

[geoffrey.tran@gmail.com](mailto:geoffrey.tran@gmail.com)

- About
	- Creative Technologist at RAPP
	- Fun with PHP since 2005
	- Contributor to Zend Framework and Symfony2
	- [http://rapp.io/1y](http://rapp.io/1y)
- Why even bother?
	- "Information leakage is one of the biggest issues that organizations are facing."
	- "93% of organizations have been hacked at least once in the past two years through insecure web applications."
	- "12% strongly agree that they have ample resources to detect and remediate insecure Web apps."
	- ...
	- "88% of respondents say their Web application security budget is less than their organization’s coffee budget."
	- State of Web Application Security, Ponemon Institute
- Top Security Risks
	- Cross-site scripting (XSS)
		- occurs when
			- data enters an application through an untrusted source, most frequently a web request
			- the data is included in dynamic content
		- types of XSS attacks
			- stored XSS attacks (persistent)
				- unknowingly retrieved by victims
			- reflected XSS attacks (non-persistent)
				- reflected off the application via an un-escaped field
		- what can an attacker do with XSS?
			- launch a phishing attack
			- steal session and cooke data to log in as the victim
			- perform unwanted actions as the victim
		- example
			- search results page
			- search term printed out to HTML without filtering
			- script tags in search field
			- MySpace "Sammy is my hero" example
				- exploit that created a new regular expression in order to get around regular expression filtering
				- exponential increase of friend requests
		- Preventing XSS
			- always validate user input
				- filter_var()
			- escape or filter all outputs
				- htmlspecialchars()
				- htmlentities()
				- strip_tags()
					- validate tag allowances
	- Cross-site Request Forgery (CSRF)
		- occurs when a victim loads a page that contains a malicious request
		- malicious because user request inherits identity and privileges of victim, forcing undesired action on victim’s behalf
			- post a tweet
			- purchase a product
		- example
			- seemingly harmless web page
			- user visits page while logged in to bank site
			- malicious page creates request on behalf of visitor to transfer funds without permission
				- <img src="othersite/action">
			- Gmail example
				- hidden form action adding a forward to another e-mail address
		- Preventing CSRF
			- require POST for actions modifying data
			- require token or "crumb" for all sensitive forms
			- crossdomain.xml
				- do not use <allow-access-from domain="*">
	- SQL Injection
		- malicious DML (data modification language)
		- beware of unescaped user input
		- use prepared statements or propert quoting instead of direct variable quoting in queries
		- example
			- MySQL.com website user dump
			- theft from financial company
	- Command Injection
		- injecting system commands
		- lack of correct input data validation
		- example
			- nslookup
				- system('nslookup ' . $host); // $host paramater unfiltered
				- system('ls ' . escapeshellarg($dir));
	- Denial of Service (DoS)
		- attempts to make service unable or degrated to users
		- Slowloris Denial of Service
			- tries to keep many connections to the server open and hold them open as long as possible
		- Preventing DoS
			- Apache
				- mod_security
				- mod_evasive
				- mod_qos
				- mod_antiloris
			- Look into proper firewalls and intrustion detection systems
	- Unnecessary Information Disclosure
		- Reduce your attack surface
			- hide displaying of errors and exceptions
			- hide exposure of PHP
				- php.ini: expose_php = Off
			- hide exposure of Apache
				- apache2.conf: ServerTokens prod
			- configure your firewall
				- don’t expose your database, search server, memcache, mail server, etc.
				- iptables

[@geoffreytran](http://twitter.com/geoffreytran)

[geoffrey.tran@gmail.com](mailto:geoffrey.tran@gmail.com)

[http://www.linkedin.com/in/geoffreytran](http://www.linkedin.com/in/geoffreytran)
