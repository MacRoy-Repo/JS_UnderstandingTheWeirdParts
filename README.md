# JS_UnderstandingTheWeirdParts

##### Nomenclature
	A : Aside | CA: Conceptual Aside | CO: Concepts | []: Reference Dir.

##### CA: Syntax Parser 
    A program that reads your code and determines what it does and if its grammar is valid.
##### CA: Lexical Environment 
    Where something sits physically in the code. A lexical Environment exists in the programming languages in which where you write something is important. Where its written and where it is surrounded.
##### CA: Execution Context 
    A wrapper that helps manage the code that is running.
##### CA: Name/ Value Pair
	Then name can be defined more than once, but can only have one value in a given execution context.
##### CA: Objects
	A collection of name/ value pairs where each value can also be a collection of name/value

##### CO: Global Environment/Global Object [GlobalEnvironmentObject]
	In the execution context(Global/ Base) of your code one Global Object and "this" variable is created by JS engine. 
	In JS GLOBAL means "Not inside a function"
	When JS code in app.js file is executed, the JS engine creates a Execution Context. At the base/global level JS engine creates :
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
##### CO: The Execution Context - Creation and Hoisting [Hoisting]
	During creation of Execution Context JS engine along with Global Object, 'this' and Outer Env. sets up a Memory space where it stores all the variables and function(intact)[Hoisting] that are	going to be used in processing the code.
		- Memory space helps to invoke a function even before it defined in the lexical env.
		- Any variable defined in the code will have to be initially placeholder(set) as  
		  'undefined' to be stored in the memory space.
	Note : The code is not physically moved to the top to invoke this feature called Hoisting rather Memory space is used to implement this feature.

	b();
	console.log(a);

	var a = 'Hello World!';

	function b() {
	    console.log("Inside b!");
	}
##### CA: 'undefined' [undefined]
	During Hoisting Phase of Context Creation : (Variable and function setup)
	When the parser in JS engine encounters a variable that is been defined it stores the variable with undefined (Special keyword/value and uses space like any other value) in the memory to be used during code execution phase. 
		
	There is a difference between 'undefined' and 'not defined'. Whenever a variable is used without defining it even once in the code then it results to 'not defined', whereas if it defined even	once and value is assigned after variable usage in the lexical environment it will result 'undefined' because the engine stores the value of variable as undefined.

	var a;
	if(a === undefined){
		console.log('a is undefined!');
	}
##### CO: The Execution Context - Code Execution [Execution]
	After creation part of Execution Context Global Object, 'this' , Outer Env. and Memory space setup the code is executed line by line sequentially
	As seen in the console output:

	app.js:2 Called b!
	app.js:6 undefined
	app.js:9 Hello World!
##### CA: Single Threaded/ Synchronous Execution
	Single Threaded - One command is executed at a time.
	In programmers prespective JS is single threaded but under the hood of the browser it may not be.
	Synchronous Execution - One line of code is executed at a time in the order it appears.
##### CO: Function Invocation and Execution Stack
	Invocation -  Running/Calling a function, In JS it is done by using parenthesis().

	function a(){
		var a;
	}
	
	function b(){
		a();
		var b;
	}

	b();
	var c;

	Internal processing of above code:
	- Global Execution Context will be created by JS Engine/Compiler(Creation Phase) during which Global object, 'this' variable, Outer enviroment and memory space contaning function a(), b() and variable b will be created.
	- Then execution of global execution context will start which in turn will invoke function b().
	- On invocation of function b(), a new Execution Context will be created on top of Global Execution Context in Execution Stack which will again go through the same creation and execution phase of an Execution Context.
	- During execution of function b(), it will encounter function a() invocation.
	- Again on invocation of a() a new Execution Context for function a() will be created on top of function b() Execution Context and will go through same creation and execution phase.
	- After function b() is executed it will be popped off the Execution Stack after which execution of function b() will start and after execution of b(), Execution Context for function b() will be popped off the Execution Stack then Global Execution Context is executed and popped off the Execution Stack. 

	So to generalize, Every function invocation creates a new Execution Context which goes through it own Creation and Execution phase. Only the top Execution Context in Execution Stack is been processed(Synchronous: One line of code at a time). It can also be noted the Lexical order of code/ Surrounding code doesnot impact the processing
	- As the code is not executed in the below sequence:
	 - b()
	 - var a;

	Where as like below:
	 - b();
	 - a();
	 - var a;
	 - var b;
	 - var c;

	During recurring calls also new EC is created on top of other everytime a call is made.
##### CO: Functions, Context And Variable Enviroments
	