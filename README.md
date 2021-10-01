
# Activity 2 from Unit 3
    
## What is a closure? 

A closure is a function that saves references to the adjacent state (lexical scope). In other words, a closure allows the scope of an outer function to be accessed from an inner function. In JavaScript, closures are created every time a function is created.

## Give me an example of closure. 

```
function counter(){
var count = 5;

function incrementCounterBy1(){
 console.log(count)
 }
	
 return incrementCounterBy1
}

const incrementCounterBy1 = counter()

incrementCounterBy1()

```

## What is ()() in code? 

It is used to access the child function found within the parent function. To put it another way is that it allows us to enter the internal function or functions within the main one.
Move the variable after the closure (the function inside the function) and explain what happens. 
Generally, nothing happens, the function and the result will continue to work as normal. What changes is the position of this declaration, because the JS programming language first reads the function and after this it reads the declaration of the variable, in addition to this, the declared function has not been executed in the program, so It doesn't matter where the variable is declared (It has to be before the function call).

```
function counter(){
   
   function incrementCounterBy1(){
      console.log(count)
   }
   var count = 5;
   return incrementCounterBy1
}

const incrementCounterBy1 = counter()

incrementCounterBy1()
```

## Change var for let and explain why the logic is not affected 

Why hoisting does not exist inside the function, so let and const behave like a var, as long as they are kept inside the parent function, since the child function can access external variables that belong to those of the father. Part of the explanation above applies in this situation as well.

```
function counter(){
    
   function incrementCounterBy1(){
       console.log(count)
   }
   let count = 5;
	    return incrementCounterBy1
}

const incrementCounterBy1 = counter()

incrementCounterBy1()

```

## Scope chain, an example of it, how many closures can we nest 

```
const language = 'brazillian portuguese'
const name = 'Ana'
	
function displayIntroduction() {
 const name = 'Maria'
  const country = 'Brazil'

function displayInfo() {
const name = 'Joana'
   console.log(`My name is ${name}, I'm from ${country} and I speak ${language}`)
  }

  return displayInfo()
}

displayIntroduction()
```

***Output: My name is Joana, I'm from Brazil and I speak brazillian Portuguese***

We can have an infinity of closures within a function, as long as we respect its hierarchy and remember its order.

## They are conflicts between the closure and the global scope? 

None, what is inside the clousure does not affect the general window, in fact there can be variables with the same name and type inside the clousure and the general window and neither of these presents problems.

```
function counter(){
    var count = 5;

    function incrementCounterBy1(){
        console.log(count)
    }
    return incrementCounterBy1
}

const incrementCounterBy1 = counter()

incrementCounterBy1()

```

## Advantages of closures. 

More security, better organization, data privacy

## ¿What is data hiding and encapsulation? 

While data hiding focuses on restricting data use in a program to assure data security, data encapsulation focuses on wrapping (or encapsulating) the complex data to present a simpler view to the user. 
In data hiding, the data has to be defined as private only. In data encapsulation, the data can be public or private. 

## Give me an example of privacy with closures. 

Languages like Java offer the possibility of declaring private methods, that is, they can only be called by other methods in the same class.

JavaScript does not provide a native way of doing this, but it is possible to emulate private methods using closures. Private methods are not only useful for restricting access to code: they also provide a powerful way to manage your global namespace, preventing non-essential methods from cluttering up the public interface of your code.

```
var Counter = (function() {
  var privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    }
  }
  })();
	
alert(Counter.value()); /* Muestra 0 */
Counter.increment();
Counter.increment();
alert(Counter.value()); /* Muestra 2 */
Counter.decrement();
alert(Counter.value()); /* Muestra 1 */ 

```

## What happens if you create two counters with the same closure? 

In this case, the memory of the counter would be shared with the two functions created within that clousure. So both can modify the results of the sister functions.

## How can we add more functions as a decrement counter? Give an example of it. 

```
function Counter(){
let counter = 0;
   this.incrementCounter = () =>{
        counter++
        console.log(counter)
    }

    this.decrementCounter = () =>{
        counter--
        console.log(counter)
    }
}
	
const counter = new Counter();

```

## What are the disadvantages of closures? 

The existence of closures brings advantages to programming with JavaScript, since we can use them to solve needs that arise. But it also creates problems: sometimes unintentional closures are generated with unwanted effects. Or sometimes an excessive number of closures are created unnecessarily, consuming resources and slowing down the execution of the code.
