# Restful APIs and Self-Building Applications

Vance Lucas

vancelucas.com

@vlucas

- Brightbit
	- http://brightb.it
	- Design, Development & Consulting for web apps, mobile apps, and APIs

## The Current State of "REST" APIs
- Most "REST" APIs
	- GET /budgets
	- simply returning data
- A Little Better
	- including URLs for HTML interactivity
	- no set way to link to something in JSON
	- many people trying to solve the linking problem, creating custom formats on top of JSON
- Even Better
	- HAL: Hypertext Application Language
	- _links { self: { href: 'http://object' } }
	- link moved to the key instead of the object itself (metadata for the JSON entry)
	- Links are better than plain data, but still *read-only*, and API documentation is still required even for basic usage.
	- An API needs to be able to write to a system, not merely reading data from it.
- What is HyperMedia? APIs?
	- martinfowler.com/articles/richardsonMaturityModel.html
	- Level 0: The Swamp of POX
		- single request/response
		- SOAP, etc.
		- all requests made via POST
		- no caching possible
	- Level 1: Resources
		- create, view, update
	- Level 2: HTTP Verbs
		- GET items
		- POST new
		- PUT update
		- etc.
	- Level 3: Hypermedia Controls
		- new level of interactivity
		- "Level 3" is a pre-condition of REST
		- Roy T. Fielding: roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven
- You *must* have hypermedia controls in your API to call it REST
	- "A REST API should be entered with no prior knowledge beyond the initial URL (bookmark) and set of standardized media types that are appropriate or the intended audience (i.e., expected to be understood by any client that might use the API). From that point on, all application state transitions must be driven by client selection of server-provided choices that are present in the received representations or implied by the user’s manipulpation of those representations." (also from roy.gbiv.com/untangled/2008/rest-apis-must-be-hypertext-driven)
- Two Key Things
	- Links
	- Forms
		- JSON Schema (on GitHub)
			- description, type, properties { propertyName { type, rules } }
		- URI Templates (RFC)
			- similar to URI routing
		- HAL Spec (DRAFT)
			- currently deals only with links
		- Link "rel" types
			- iana.org/assignments/link-relations/link-relations.xml
- NO official spec for linking or describing resources for JSON or XML
- Consistency is the *most important thing*.
- Demo
	- _links, _self, relType
	- Titanium (JS)
	- simple budget application
		- REST API (HyperMedia)
		- iPhone application
		- github.com/vlucas

[http://joind.in/6347](http://joind.in/6347)

HAL Discuss Group: [http://groups.google.com/group/hal-discuss](http://groups.google.com/group/hal-discuss)

API Craft Group: [http://groups.google.com/group/api/api-craft](http://groups.google.com/group/api/api-craft)
