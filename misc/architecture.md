# Architecture

## Web concepts

* [Tokens, sessions and cookies](https://www.youtube.com/watch?v=44c1t_cKylo)

## Misc concepts

* Polymorphism
* Reflection
* Active Record vs. Data Mapper (ORMs)

## Reactive programming

* [Intro to Reactive Programming](https://www.youtube.com/watch?v=Bme_RiT9CK4)

  **Core concepts**

* Remove duplicated state
* Derived state

## Closures

* A form of data encapsulation
* Similar to an object, but with (usually) just a single method

```javascript
function make_greeter(msg) {
    function greet(name) {
        console.log(msg + " " + name + "!");
    }
    return greet;
}
helloer = make_greeter("Hello");
high_fiver = make_greeter("High five");
helloer("Markus");
high_fiver("Markus");
```

## Class-based vs. Prototype-based object orientation

* Class: A template for instantiating objects
* Prototype: A base object referenced by an object
* Methods: Defined on the class or on the protoype object
