# A Soft Introduction to Machine Learning

Joël Perras

[@jperras](http://twitter.com/jperras)

- Math
	- predictive analyses based on given inputs
	- computers do not have intuition
	- algorithms must be specifically programmed
- Broad Categories of Machine Learning & Graph Theory
	- Graphs & Matrices
		- Graphs
			- vertex
				- (aka node, point, junction, 0-simplex)
				- visually represented by a circle
			- edge
				- (aka arc, branch, line, link, 1-simplex)
				- visually represented by a line
				- possibly including an arrow
				- one arrow = directed edge
				- no arrow or two arrows = undirected edge
				- can have weights or capacities
				- Ford-Fulkerson: network flow analysis research
			- graph simply a collection of edges and nodes
			- Types of Graphs
				- Simple (at most one edge between any pair of nodes)
				- Multigraph (multiple edges between same vertices allowed)
		- Vectors & Points
			- Vertex and points allow Amazon to recommend books, and Netflix to recommend films.
			- "features"
			- "center" point and distance from another point
		- Matrix
			- two-dimensional (or multi-dimensional) structure
	- Binary Classification
		- one or the other (good vs. bad, true vs. false, etc.) 
	- Bayesian Networks (Probablity of X, given Y)
		- given a coin toss with a result, what is the probablity of the other result on the next toss?
		- etc.
	- Decision Trees
		- trees of outcomes, costs, and expected values
	- Support Vector Machines
		- maximum margin hyperplanes
	- Artificial Neural Networks
		- model things according to the structure of the human brain
	- Regression
		- linear classification instead of binary classification
	- Linear Regression
	- Logistic Regression
	- Clustering
		- extracting natural or artificial clusters from a data set
		- select random points
		- identify distance to surround points
		- find the average distance in order to obtain a center point
		- group items based on closest distance
	- Supervised vs. Unsupervised
		- supervised: human-assigned labels
		- unsupervised: no human-assigned labels
	- Matchings & Network Flows
		- BJCP (Beer)
			- beer judging organization
			- 70 judges, 28 categories
			- at least 2 judges per category
		- Recommenders
			- Amazon (books)
			- Pandora (music)
			- Hunch (various)
			- Yelp (food)
			- LinkedIn (netowrking)
			- Netflix (films)
			- users + items (identifying graphic databases)
		- graph databases
			- neo4j, others
		- colummn-oriented databases
			- hbase, cassandra
		- Essential (Python) Libraries
			- numpy, scipy, scikits, etc.
- References
	- Intro to Algorithms (MIT)
	- Flows in Networks
	- The Algorithm Design Manual
	- many more

[@jperras](http://twitter.com/jperras)

[@FictiveKin](http://twitter.com/fictivekin)
