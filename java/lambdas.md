# Inner classes and lambdas

* Tutorial: [Jenkov Tutorials](http://tutorials.jenkov.com/)

## Variants

* Multiple \(non-nested\) classes in a single .java file
* Inner class: Has access to members of the outer class
* Static inner class: Has access to \(only\) static members of the outer class
* Anonymous class
  * Has access to final variables of the current scope   
* Method-level class
  * Has access to final variables of the current scope 

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.Comparator;
import java.util.List;

public class Sorting {

    public String text = "Sorter";

    public static void main(String[] args) {
        List<String> items = Arrays.asList("Martin", "Bert", "Markus");

        // standard class
        Collections.sort(items, new StandardComparator());

        // static inner class
        Collections.sort(items, new InnerComparator1());

        // non-static inner class
        new Sorting().sort();

        // anonymous inner class
        Collections.sort(items, new Comparator<String> () {                    
            @Override
            public int compare(String s1, String s2) {
                return s1.length() - s2.length();
            }
        });

        // lambda (variant 1)
        Collections.sort(items, (String s1, String s2) -> {
            return s1.length() - s2.length();
        });

        // lambda (variant 2)
        Collections.sort(items, (s1, s2) -> {
            return s1.length() - s2.length();
        });

        // lambda (variant 3)
        Collections.sort(items, (s1, s2) -> s1.length() - s2.length());
    }

    public void sort() {
        // non-static inner class (not possible in static methods)
        List<String> items = Arrays.asList("Martin", "Bert", "Markus");
        Collections.sort(items, new InnerComparator2());
    }

    public static class InnerComparator1 implements Comparator<String> {

        @Override
        public int compare(String s1, String s2) {
            return s1.length() - s2.length();
        }
    }

    // a non-static inner class instance holds a reference to the enclosing instance
    public class InnerComparator2 implements Comparator<String> {

        @Override
        public int compare(String s1, String s2) {
            return s1.length() - s2.length();
        }
    }
}
```

```java
import java.util.Comparator;

public class StandardComparator implements Comparator<String> {

    @Override
    public int compare(String s1, String s2) {
        return s1.length() - s2.length();
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

(String s) -> Integer.parseInt(s)
Integer::parseInt // static method reference
```

## Streams

* [http://tutorials.jenkov.com/java-functional-programming/streams.html](http://tutorials.jenkov.com/java-functional-programming/streams.html)
* [https://www.sitepoint.com/java-8-streams-filter-map-reduce/](https://www.sitepoint.com/java-8-streams-filter-map-reduce/)
* [https://www.simplilearn.com/what-is-mapreduce-and-why-it-is-important-article](https://www.simplilearn.com/what-is-mapreduce-and-why-it-is-important-article)
