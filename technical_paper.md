# Design Pattern

## Abstract

Every Software Engineer wants to write a code that is easy to manage, readable, reusable and well structure but sometimes writing these kinds of codes become harder. If we are working on an application then we have to write lots of code but managing that kind of code become very hard. In this paper, we will get to know about the idea of how to solve this problem with the help of **design patterns in JavaScript**.

## Introduction

A design pattern provides a general reusable solution for the common problems that occur in software design. By using it we can make our code more flexible, reusable, and maintainable. We can also look at design patterns as a template or a blueprint one can easily create different objects by using this blueprint just like from a blueprint of houses we can build as many houses we want the same case it works with Design Pattern also. In this paper, we will learn about how to use these Design patterns in the field of web development and we all know JavaScript is the best for completing this task so in this we will see about five different kinds of design Pattern which is used in JavaScript.

## Content

We have various kinds of design patterns, but here we will discuss only  five different types of Design Patterns with codes in JavaScript, which are  

* Module Design Pattern
* Prototype Design Pattern
* Singleton Design Pattern
* Constructor Design Pattern
* Factory Design Pattern  

### **Module Design Pattern**

Module Design Pattern is the most used design pattern in JavaScript. In this design pattern, we keep a particular piece of code independent from other components of codes. It is similar to the **classes** in object-oriented programing. In OOP, we have four major components and, one of them is **encapsulation** which helps the classes to make private attributes this is the thing which we use in this pattern. In this pattern, we use **Immediately Invoked Function Expression (IIFE)** to allow a private scope that is independent of the global scope. As this pattern was created it was immediately invoked without calling it from global. It helps us to create private attributes which can't be accessed by global but if we want we can give the access of calling a method or function from global using return statement.

```
(function(){

    // for declaring private variable and method

    return{

        // for declaring public variable and method 

    }
})()
```

This is the basic syntax of this module. In this, we don't have to create an instance for calling this function it is automatically called by itself.

```
const Dog = (function(){
    const breed = 'Pitbull'
    const doBark = function(){
        console.log('BARK BARK BARK')
    }

    return {
        speak : function(){
            doBark()
            console.log(breed)
        }
    }
})()

Dog.speak()
/* Output : 
'BARK BARK BARK' 
'Pitbull'*/

console.log(Dog.breed)
/*output :
undefined*/
```

In this example, we can see that when we call Dog.breed it shows us undefined because the breed is declared in private scope but when we call the speak function its work because it is a return block.

### **Prototype Design Pattern**

Prototype Design Pattern, as the name suggested it relies on the **Prototypical Inheritance** in JavaScript, which is also a component of OOP. This design pattern is generally used for creating objects in a performance-intensive situation or making the object more advance. The object, which is created is cloned of the previous or original one which is passed to it this helps us not to create a new object from scratch, which consume more resource. It helps us to create a new instance from the existing instance. We can create a clone of an instance by using a method name as **prototype**.

```
var object = function(){

    // For creating an object

}

object.prototype = (function(){

    //For creating a prototype of object or creating a modyfying version of it

})()
```

This is the basic syntax of prototype inheritance. In this, we create an object, and after that, we create a prototype of it using the prototype method 

```
const Dog = function(){
    this.colour = 'Brown'
    this.breed = 'Pug'
    this.name = 'Yuki'
    console.log('BARK')
}

Dog.prototype ={
    bark : function(){
    console.log('BARK BARK BARK')
    }
}

Dog.prototype.swim = function(){
    console.log(this.name + ' is swimming')
}

Test = new Dog()
// Output : BARK

Test.bark()
// Output : BARK BARK BARK

Test.swim()
// Output : Yuki is swimming
```

In this example, we can see that constructor allow us to create a new object of Dog while retaining its state.

### **Singleton Design Pattern**

Sometimes creating only a single instance is better than creating multiple for example, if we connect a single database to multiple objects makes things cheaper instead of connecting to every object. Similarly, if a six-person family has only parking for one car in their home, they will buy only one, and all the people, use the same car since there is no parking for the second car.

Singleton Design Pattern, as the name, contains single, which refer to the single instantiation. _A singleton pattern is a design pattern that restricts the instantiation of a class to one object_.

```
const car= (function(){
  let carInstance

  function start(){

      function gearup(){
          console.log('Gear is up')
      }

      function geardown(){
          console.log('Gear is down')
      }

      function reverse(){
          console.log('Car is moving in reverse order')
      }
      return {
          gearup : gearup,
          geardown : geardown,
          reverse : reverse
      }
  }

  return{
      getInstance: function(){
          if (!carInstance){
              carInstance = start()
          }
          return carInstance
      }
  }
})()

const swift = car.getInstance()
swift.gearup()
// Output : Gear is up

swift.reverse()
// Output : Car is moving in reverse order
```

In this car example, we create start methods in private because we do not want the user to access them, because if the user gets access to it, then it can create the new object by itself however if you notice user can create an instance of the car but for creating that it has to interact with getInstance method which works only on the single instance which is carInstance. So by this way, Singleton works. 

### **Constructor Design Pattern**

Constructor Design Pattern, as the name suggested it relies on a **constructor** method which we also called an initializer. In object-oriented programming languages, a constructor is a special method used to initialize or add a property in a newly created object once the memory has been allocated for it. If we create objects of the class car then all the cars have some properties for eg - colour, name, max speed etc.

Object constructors are used to create specific types of objects - both preparing the object for use and accepting arguments which a constructor can use to set the values of member properties and methods when the object is first created. 

```
function Car(){

}

const swift = new Car()
swift.colour = 'White'
console.log(swift.colour)
// Output : White

const Nexa = new Car()
Nexa.colour = 'Black'
console.log(Nexa.colour)
// Output : Black
```

In this example, we create a function Car and its two objects _swift_ and _Nexa_. Now after creating these two objects, I have to mention a single property of colour two times one in the _Nexa_ and another in the _swift_ so here in these types of cases our constructor design pattern helps.

```
function Car(colour,maxSpeed){
    this.colour = colour
    this.maxspeed = maxSpeed

}

const swift = new Car('White',150)
console.log(swift.colour)
// Output : White

const Nexa = new Car('Black',180)
console.log(Nexa.colour)
// Output : Black
```

In this example, we can see that we declare these properties inside the function with the help of the constructor and this helps us to not write the syntaxes and again for every new object we just add the value in the constructor (Here "this" keyword is represented to the object).

### **Factory Design Pattern**

The Factory Design pattern is another type of **creational design pattern** just like the constructor design pattern. As the name suggested Factory which refers to creating and building it also creates the new object but in a different way than the constructor one. In this design pattern, _we create an interface for creating a new object, in which we just have to specify its type or property._ In this method, we do not create the object with the help of the constructor because sometimes creating an instance for each type become complex like in a factory many people are working in various fields so sometimes creating the object of every person become complex because there are so many objects to handle if I want the name of the people who are working in developing field and the whole team has a thousand members so knowing all these names will be difficult so at this case, we use Factory Design Pattern.

```
function Factory(type,name){
    this.type = type
    this.name = name
}

Rahul = new Factory('developer','Rahul')
Himanshu = new Factory ('developer','Himanshu')
Shubhi = new Factory('developer','Shubhi')
Sachin = new Factory('Sales','Sachin')
```

In this example, we created a function Factory which has an attribute of type and name and after that there are four different objects but three have the same type, developer. Now if I give a task to these developers I have to know the name of the object which are in this field since there are only four employees so remembering their name is not a big deal but if there are a thousand then remembering their name is a big deal so for solving this problem we use Factory pattern.

```
function Developer(name){
    this.type = 'Developer'
    this.name = name
}

function Sales(name){
    this.name= name
    this.type= 'Sales'
}

function Factory(){
    this.create = function (name,type){
        switch(type)
        {
            case 1:
                return new Developer(name)
                
            case 2:
                return new Sales(name)
        }
    }
}

function say(employee){
    console.log(`Hi my name is ${employee.name} and I am a ${employee.type}`)
}

const employeeFactory = new Factory()
const employees = []
employees.push(employeeFactory.create('Rahul',1))
employees.push(employeeFactory.create('Himanshu',1)) 
employees.push(employeeFactory.create('Shubhi',1))
employees.push(employeeFactory.create('Sachin',2))

employees.forEach(say)
/*Output : 
Hi my name is Rahul and I am a Developer
Hi my name is Himanshu and I am a Developer
Hi my name is Shubhi and I am a Developer
Hi my name is Sachin and I am a Sales   */
```

In this, I create an object with the help of an 'employee factory' which interacts with the function 'Factory' for creating the object and stores the object into an array 'employee'. Here we can see that we don't have to create an instance for each employee this is the benefit of it. 

## Conclusion

Design patterns are frequently used in building applications because they make code short, readable and easy maintainable but before using it think about the advantages and disadvantages of these design patterns because every design pattern has its own advantages and disadvantages on others and thoroughly think which will help you in building your application after that chose you pattern whether it is a **module, singleton, constructor, factory or prototype** etc because after that what you choose is the best.  