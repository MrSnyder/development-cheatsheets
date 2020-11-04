# Java Basics

* Tutorial: [Jenkov Tutorials](http://tutorials.jenkov.com/)

## Inner, anonymous classes and lambdas

Where does this appear?

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Sorting {

    public String text = "Sorter";

    public static void main(String[] args) {
        List<String> items = Arrays.asList("Martin", "Bert", "Markus");
        System.out.println("Before: " + items);
        // sort is a static method of class Collections

        // "normal" class
        Collections.sort(items, new StandardComparator());

        // static inner class
        Collections.sort(items, new InnerComparator1());

        // non-static inner class (this is not allowed in static methods!!!)
        // Collections.sort(items, new InnerComparator2());

        // anonymous class
        // how to spot it:
        // new TypeName () { ... }
        //  ^     ^            ^
        //  a     b            c
        // a: new must be present
        // b: usually the name of an Interface
        // c: has an implementation block
        //
        // advantage: briefest way
        // disadvantage: can not be re-used
        // disadvantage: has no describing name
        Collections.sort(items, new Comparator<String> () {                    
            @Override
            public int compare(String s1, String s2) {
                if (s1.length() > s2.length()) {
                    return 1;
                }
                if (s1.length() < s2.length()) {
                    return -1;
                }
                return 0;
            }
        });

        // lambda (variant 1)
        Collections.sort(items, (String s1, String s2) -> {
            if (s1.length() > s2.length()) {
                return 1;
            }
            if (s1.length() < s2.length()) {
                return -1;
            }
            return 0;
        });

        // lambda (variant 2)
        Collections.sort(items, (s1, s2) -> {
            if (s1.length() > s2.length()) {
                return 1;
            }
            if (s1.length() < s2.length()) {
                return -1;
            }
            return 0;
        });

        // lambda (variant 3)
        Collections.sort(items, (s1, s2) -> s1.length() - s2.length());

        // equivalent anonymous class
        Collections.sort(items, new Comparator<String> () {                    
            @Override
            public int compare(String s1, String s2) {
                return s1.length() - s2.length();
            }
        });

        System.out.println("After: " + items);
    }

    public void doSomething() {
        List<String> items = Arrays.asList("Martin", "Bert", "Markus");
        Collections.sort(items, new InnerComparator2());
    }

    public static class InnerComparator1 implements Comparator<String> {

        @Override
        public int compare(String s1, String s2) {
            if (s1.length() > s2.length()) {
                return 1;
            }
            if (s1.length() < s2.length()) {
                return -1;
            }
            return 0;
        }
    }

    // a non-static inner class instance has a reference to the enclosing instance
    public class InnerComparator2 implements Comparator<String> {

        @Override
        public int compare(String s1, String s2) {
            if (s1.length() > s2.length()) {
                return 1;
            }
            if (s1.length() < s2.length()) {
                return -1;
            }
            return 0;
        }
    }
}
```

```bash
import java.util.Comparator;

public class StandardComparator implements Comparator<String> {

    @Override
    public int compare(String s1, String s2) {
        if (s1.length() > s2.length()) {
            return 1;
        }
        if (s1.length() < s2.length()) {
            return -1;
        }
        return 0;
    }

}
```

## Lambdas

* An anonymous function used as a parameter
* Code to be executed "later" \(not evaluated immediately\)
* [Jump-Starting Lambda Programming](https://stuartmarks.files.wordpress.com/2014/09/tut3371-marks-jumpstartinglambda.pdf)

### Functional interfaces

Functional interfaces are interfaces with a single-method:

```java
// from java.util.function
interface Predicate<T> {
    boolean test(T t);
}

interface Consumer<T> {
    void accept(T t);
}

interface Function<T, R> {
    R apply(T t);
}
```

### Lambda examples

Lambda expressions can be used wherever an instance of a functional interface is required.

```java
// expression lambdas
(int a, int b) -> a + b
(int a) -> a + 1    
() -> 42

// statement lambdas
(int a, int b) -> { println(a + b); return a + b; }    
(int a) -> { println(a + 1); return a + 1; }    
() -> { println("Returning 42."); return 42; }

// method references
(Person p) -> p.toString()
Person::toString // unbound method reference

(String    s) -> Integer.parseInt(s)
Integer::parseInt // static method reference
```

## Streams

* [http://tutorials.jenkov.com/java-functional-programming/streams.html](http://tutorials.jenkov.com/java-functional-programming/streams.html)
* [https://www.sitepoint.com/java-8-streams-filter-map-reduce/](https://www.sitepoint.com/java-8-streams-filter-map-reduce/)
* [https://www.simplilearn.com/what-is-mapreduce-and-why-it-is-important-article](https://www.simplilearn.com/what-is-mapreduce-and-why-it-is-important-article)

## Inner / nested classes

* Multiple \(non-nested\) classes in a single .java file
* Inner class: Has access to members of the outer class
* Static inner class: Has access to \(only\) static members of the outer class
* Anonymous class
  * Has access to final variables of the current scope   
* Method-level class
  * Has access to final variables of the current scope 

