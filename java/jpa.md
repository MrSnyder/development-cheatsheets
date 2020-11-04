# JPA Cheatsheet

## Minimal entity class mapping

Steps
  * Required: Annotate class with @Entity
  * Required: Define field with @Id annotation
  * NOTE: Prefer Lombok for automatic Getter/Setter generation.  

```java
@Entity
@Setter
@Getter
public class Book {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;
}
```

## One-to-many mapping

Steps
  * Identify many side and annotate entity field (see below)
  * Annotate field (Set/List) on opposing entity side (see below)
 
```java 
@Entity
public class Book {
    @ManyToOne
    private Publisher publisher;
}

@Entity
public class Publisher {
    // HINT: refers to Book#getPublisher
    @OneToMany(mappedBy="publisher")
    private Set<Book> books;
}
``` 

## Many-to-many mapping (without attributes)

Steps
  * Identify owning side and annotate entity field (see below)
  * Annotate field on opposing entity side (see below)
 
```java 
@Entity
public class Author {
    // owning side
    @ManyToMany
    private Set<Book> books;
}

@Entity
public class Book {
    // inverse side
    @ManyToMany(mappedBy = "books")
    private Set<Author> authors;
}
```
### Caveats
* Only the owning side is considered for saving join table rows: https://stackoverflow.com/questions/14111607/manytomanymappedby-foo

### Set or List?

It's usually preferrable to use Set:

* If one uses List (on one or two sides of the asscociation) in the examples above, the join table will not have a primary key (using two Sets it will be a composite PK made up of the two foreign keys). This makes the relations to the join table *identifiying* (a pair of FKs identifies a row) and prevents the insertion of multiple rows with the same values.
* Additionally, it has performance benefits when deleting associations between the two entities: https://vladmihalcea.com/the-best-way-to-use-the-manytomany-annotation-with-jpa-and-hibernate/

## Many-to-many mapping (with attributes)

Steps
  * Create entity for JoinTable
  * Annotate fields in JoinTable entity (see below)
  * Annotate field opposing side 1 (see below)
  * Annotate field opposing side 2 (see below)
 
```java
@Entity
@Table(name = "customer_order")
public class Order {

	@ManyToOne
	private Book book;
	
	@ManyToOne
	private Customer customer;

	private Integer amount;

}

@Entity
public class Book {
    @OneToMany(mappedBy = "book")
    private Set<CustomerOrder> orders;
}

@Entity
public class Customer {
    @OneToMany(mappedBy = customer")
    private Set<CustomerOrder> orders;
}
```