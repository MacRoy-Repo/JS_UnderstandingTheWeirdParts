# JS_UnderstandingTheWeirdParts

#### Conceptual Aside
##### Syntax Parser 
    A program that reads your code and determines what it does and if its grammar is valid.
##### Lexical Environment 
    Where something sits physically in the code. A lexical Environment exists in the programming 
    languages in which where you write something is important. Where its written and where it is 
    surrounded.
##### Execution Context 
    A wrapper that helps manage the code that is running.
##### Name/ Value Pair
	Then name can be defined more than once, but can only have one value in a given execution 
	context.
##### Objects
	A collection of name/ value pairs where each value can also be a collection of name/value

#### Concepts
##### Global Environment/Global Object
	In the execution context(Global/ Base) of your code one Global Object and "this" variable 
	is created by JS engine. 
	In JS GLOBAL "Not inside a function"
	When JS code in app.js file is executed, the JS engine creates a Execution Context. At the base/
	global level JS engine creates :
			- Global Object (window object in case of browser)
			- 'this' : Special variable. At global level 'this' and global object are same
			- Outer Environment : In case of function how code communicates with global Object
			- Then Our piece of code.
	Note : Anything we write in code a variable/ function while execution gets stored in the 
	key/value fashion in global object. So in case of browser the varaible and function could be 
	accessed using :

	window.a;
	"Hello World"
		
	window.b;
	f(){
	} 
