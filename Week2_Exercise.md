# Week 2 Exercises
This is a reference of Code for Week 2 Exercise.

## Week 2 Unit 1 Excercise

### Define Aspect
```cds
namespace com.bookshop;

aspect additionalInfo {
    name: String (120);
}

entity Books {
    key ID      : Integer;
    title       : String(100);
    stock       : Integer;
    price       : Decimal(9,2);
    author      : Association to Authors;
    publisher   : Association to Publishers;
}

entity Authors: additionalInfo {
    key ID  : Integer;
    books   : Composition of many Books on books.author = $self;
}

entity Publishers: additionalInfo {
    key ID  : Integer;
    books   : Composition of many Books on books.publisher = $self;
}
```

### Include new Entity in Service Definition
```cds
entity Publishers as projection on bookshop.Publishers;
```

### Add Initial Data to Publisher entity

Publisher:
```csv
ID;name
300;Charles Scribner's Son
301;Penguin Random House
302;The Hogarth Press
303;Blas de Robles
304;Charles Scribner's Sons
```

Books:
```csv
ID;title;stock;price;author_ID;publisher_ID
100;The Great Gatsby;10;500;200;300
101;Invisible Man;50;400;201;301
102;To the Lighthouse;5;385;202;302
103;Don Quixote;2;600;203;303
104;The Sun Also Rises;100;300;204;304
```
