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
	name/value pair in global object. So in case of browser the varaible and function could be 
	accessed using :

	window.a;
	"Hello World"
		
	window.b;
	f(){
	} 
##### The Execution Context - Creation and Hoisting
	During creation of Execution Context JS engine along with Global Object, 'this' and Outer Env. 
	sets up a Memory space where it stores all the variables and function(intact)[Hoisting] that are 
	going to be used in processing the code.
		- Memory space helps to invoke a function even before it defined in the lexical env.
		- Any variable defined in the code will have to be initially placeholder(set) as  
		  'undefined' to be stored in the memory space.
	Note : The code is not physically moved to the top to invoke this feature called Hoisting rather
		   Memory space is used to implement this feature.

	b();
	console.log(a);

	var a = 'Hello World!';

	function b() {
	    console.log("Inside b!");
	}
##### 'undefined'
	During Hoisting Phase of Context Creation : (Variable and function setup)
	When the parser in JS engine encounters a variable that is been defined it stores the variable 
	with undefined (Special keyword/value and uses space like any other value) in the memory to be 
	used during code execution phase. 
		
	There is a difference between 'undefined' and 'not defined'. Whenever a variable is used without
	defining it even once in the code then it results to 'not defined', whereas if it defined even 
	once and value is assigned after variable usage in the lexical environment it will result 
	'undefined' because the engine stores the value of variable as undefined.

	var a;
	if(a === undefined){
		console.log('a is undefined!');
	}