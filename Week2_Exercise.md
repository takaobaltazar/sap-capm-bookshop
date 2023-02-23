# Week 2 Exercises
This is a reference of Code for Week 2 Exercise.

## Table of Contents
1. [Week 2 Unit 1 Excercise](##week-2-unit-1-excercise)
2. [Week 2 Unit 2 Excercise](##week-2-unit-2-excercise)

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

## Week 2 Unit 2 Excercise

### Import Common Aspects
```cds
namespace com.bookshop;
using { managed, cuid } from '@sap/cds/common';

aspect additionalInfo {
    name: String (120);
}

entity Books: managed, cuid {
    title       : String(100);
    stock       : Integer;
    price       : Decimal(9,2);
    author      : Association to Authors;
    publisher   : Association to Publishers;
}

entity Authors: additionalInfo, managed, cuid {
    books   : Composition of many Books on books.author = $self;
}

entity Publishers: additionalInfo, managed, cuid {
    books   : Composition of many Books on books.publisher = $self;
}
```

### Add new HTTP Request
```http
POST http://localhost:4004/admin/Authors
Content-Type: application/json

{
    "name": "John Doe",
    "books": [{
        "title": "Book of John Doe",
        "stock": 100,
        "price": 550.00
    }]
}
```

## Week 2 Unit 3 Excercise

### Add Access Control
```cds
using { com.bookshop as bookshop } from '../db/domain-model';

service AdminService {
    @insertonly
    entity Books as projection on bookshop.Books;
    entity Authors as projection on bookshop.Authors;
    entity Publishers as projection on bookshop.Publishers;
    
    action submitOrder (bookId: Books:ID, quantity: Integer);
}
```

### Add Input Validation
```cds
namespace com.bookshop;
using { managed, cuid } from '@sap/cds/common';

aspect additionalInfo {
    name: String (120);
}

entity Books: managed, cuid {
    title       : String(100) @mandatory;
    stock       : Integer;
    price       : Decimal(9,2);
    author      : Association to Authors;
    publisher   : Association to Publishers;
}

entity Authors: additionalInfo, managed, cuid {
    books   : Composition of many Books on books.author = $self;
}

entity Publishers: additionalInfo, managed, cuid {
    books   : Composition of many Books on books.publisher = $self;
}
```

### Add New GET HTTP Request
```http
GET http://localhost:4004/admin/Books
Content-Type: application/json
```

### Add New POST HTTP Request

```http
POST http://localhost:4004/admin/Books
Content-Type: application/json

{
    "title": "",
    "stock": 100,
    "price": 550.00
}
```
