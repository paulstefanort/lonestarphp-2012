# It Was Like That When I Got Here

Paul Jones

[joind.in/6700](http://joind.in/6700)

[auraphp.github.com](http://auraphp.github.com)

[paul-m-jones.com](http://paul-m-jones.com)

[@pmjones](http://twitter.com/pmjones)

## Steps Toward Modernizing A Legacy Codebase

[joind.in/6700](http://joind.in/6700)

[paul-m-jones.com](http://paul-m-jones.com)

Books
- Refactoring (Martin Fowler)
- The Mythical Man-Month (Fred Brooks)
        - Brooks’ Law (adding people to a late project makes it later)
- The Road Less Traveled (M. Scott Peck, MD)

About
- 8 years USAF Intelligence
- PHP since 1999
- Developer, Senior Developer, Team Lead, Architect, VP of Engineering
- Aur project, benchmarking series, SOlar framework, Svant template system, Zend_DB, Zend_View
- PEAR group member, ZCE advisor, PHP-FIG voting member

Overview
- It was like that when I got there
- Paying off techincal debt
- Life is easier (but not perfect)

It was like that when I got there
- Messy Codebase
        - Spaghetti include logic
        - Few or no classes
        - Global variables
        - No unit tests -- QA working overtime
- No Time To Remedy
        - Bugs to fix, _right now_
        - Features to implement, _right now_
        - Making your own life easier? Not a priority.
        - Dig in and try to make do
        - How did it get this bad? "It was like that when I got here."
- The Great Thing about PHP ...
        - ... is that anyone can use it.
        - Have an idea? Implement it!
        - It works! Great success!
        - ... it "works"
- The Awful Thing About PHP ...
        - ... is that anyone can use it.
        - The codebase is like a "dancing bear"
        - Architecture? Maintenance? Testing?
        - Move on to the next idea ...
        - but *you* are stuck with it now.
- Project Evolution Tracks
        - Starting out
                - One-Off Heap
                        - No discernible architecture
                        - Browse directly to scripts
                        - Add to it piece by piece
                        - Little to now separation of concerns
                        - Global variables
                - Standalone App
                        - One-off heap ++
                        - Page scripts and common includes
                        - Installed in web root
                        - Responsible for global execution environment
                        - Script variables still global
        - Other consistent tracks of development
- Why Is It Like This?
        - Original developer probably didn’t know better
        - Subsequent developers worked with what was there
        - "We can fix it later; we need this done now."
        - (later never comes)
- Technical Debt
        - all the things that should have been done but were not done, and are now causing problems
- Paying Off Technical Debt
        - A lot like paying off financial debt
        - Got the stuff first, but have to pay for it eventually
        - No easy way out. Suffer as things are, or suffer through change.
- Big-Bang Approach
        - Rewrite from scratch!
        - "It’s the only way to be sure."
        - Expend effort while not earning revenue
        - End up with different bad architecture
        - (double your estimate, and then convert it to the next highest unit; 2 months becomes 4 years)
- Incremental Approach
        - Small changes across entire codebase
        - Build on previous small changes
        - Keeps running the whole time
- Incremental Goals
        - Stop digging! (When you are in a hole... Mark Twain?)
        - Keep the application running
        - Consolidate classes for autoloading (PSR-0)
        - Convert globals to injected dependencies
- Consolidate Classes for Autoloading
        - automatically loading files
        - spl_autoload_register(’auto_loading_function’)
- PSR-0
        - Class name maps directly to file name
        - Namespace separators map to directory separators
        - Class underscores map to directory separators
        - Vendor\Package_Name\Exapmle_Name => Vendor/Package_Name/Example/Name.php
- Move Class Files
        - If you have class files in several paths, move them to the same base path
        - If you have more than one class per file, split into separate files
        - If you define classes as part of a script, extract to own file
        - Remofe _include/require_ as you go (grep)
        - If needed, chang enames as you go (grep)
- Convert Function FIles to Class Files
        - Many projects have files of function definitions
        - Wrap in a class as static or instance methods
        - Move to classes directory
        - Change calls to static or instance calls (grep)
        - Remove _include_/_require_ as you go (grep)
- Convert Globals to Injected Dependences
        - Instantiating Dependencies in Methods
                - one-off call (database connection, etc.)
        - Drawbacks
                - New connection on each call
                - Cannot reuse connection
                - Parameter modification
- Dependency Injection
        - Instead of reaching out from inside the class to bring out dependencies ...
        - ... inject the dependency into the class from the outside.
        - Starting Point: Global In Method
                - referencing global variable in method
        - Interim: Global in Constructor
                - referencing global variable in constructor, setting member
        - Final: Dependency Injection
                - move global from constructor to constructor parameter
- Change Instantiation Calls
        - Must change all new instantiations to pass dependencies (grep)
        - Class instantiation inside methods? Pass intermediary dependencies.
- Intermediary Dependency
        - dependencies may need to be passed through multiple levls
        - violates law of demeter; pass only what a class needs, not caring about what a subcless might need
        - de-couple classes to maintain dependency injection
- Life After Reorganizing
        - Initial Goals Completed ...
                - Consolidated into classes with PSR-0 and autoloading
        - ... But Much Remains
                -  individual scripts
                - no testing
        - It’s better than before
                - easier to test existing classes
                - organizational structure for future work
                - significant technical debt paid off

[joind.in/6700](http://joind.in/6700)

[auraphp.github.com](http://auraphp.github.com)

[paul-m-jones.com](http://paul-m-jones.com)

[@pmjones](http://twitter.com/pmjones)
