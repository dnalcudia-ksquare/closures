# Activity 2: Closures
## ¿What is a closure? 
a function inside another function that has access to the variables and parameters of the outside function.

## Give me an example of closure. 
  const add = (function () {
	  let counter = 0;
	  return function () {counter += 1; return counter}
	})();

	add();

## What is ()() in code?
directly access the function within the other function.

## Move the variable after the closure (the function inside the function) and explain what happens. 
it works as long as the variable is before the return because the closure was declared, but has not been called.

## Change var for let and explain why the logic is not affected 
it works, in this case changes in scope or hoisting do not influence the behavior of the logic.

## Scope chain, an example of it, how many closures can we nest  is infinite as long as the correct structure of the closure is followed.
	const add = (function () {
	let counter = 0;
	return function () {counter += 1; return function() {counter+=1; return function(){counter+=1; return counter;}}}
	})();
	function myFunction(){
	  document.getElementById("demo").innerHTML = add()()();
	}
  
## They are conflicts between the closure and the global scope?
there isn't, doesn't exist because variables inside closure are block scoped so no problem with

## Advantages of closures.
Data hidding, encapsulation, privacy, first-class functions, and so on and so on.

## ¿What is data hiding and encapsulation?
Data bidding: hide global variables within functions to avoid a security breach
Encapsulation: encapsulation is the idea that an object should not be directly exposed

## Give me an example of privacy with closures. 
function createAnimal(name, job) {
  //private variables
  let _name = name;
  let _job = job;

 return {
   getName() {
      return _name;
    },
    getJob() {
      return _job;
    },
   setName(newName) {
      _name = newName;
    },
    setJob(newJob) {
      _job = newJob;
    }
  };
}

## What happens if you create two counters with the same closure? 
if we create a count variable in the global scope it does not interfere with what happens in the closure.
If we create another instance of the closure we now have two variables count = 0, however both act independently of the other, changing only if their methods are called, at least in the example that I show below

## How can we add more functions as a decrement counter? Give an example of it. 
Adding "methods and attributes" similar to those of a class. Something like the example I put on data privacy.
function counter() {
 var count = 0

 return {
   increment() {count += 1; console.log(count)},
   decrement() {count -= 1; console.log(count)}
  };
}
var x = counter()
x.increment()
x.increment()
x.increment()
x.decrement()

## What are the disadvantages of closures? 
closures have a negative impact on script performance, including processing speed and memory consumption.
