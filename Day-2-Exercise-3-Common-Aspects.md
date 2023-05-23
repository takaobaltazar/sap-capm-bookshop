# Day 2 Exercise 3
This is a reference of Code for Day 2 Exercise 3

## Import Common Aspects
```cds
namespace com.bookshop;

using {
    managed,
    cuid
} from '@sap/cds/common';

aspect additionalInfo {
    name : String(120);
}

entity Books : managed, cuid {
    title     : String(100);
    stock     : Integer;
    price     : Decimal(9, 2);
    author    : Association to Authors;
    publisher : Association to Publishers;
}

entity Authors : additionalInfo, managed, cuid {
    books : Composition of many Books
                on books.author = $self;
}

entity Publishers : additionalInfo, managed, cuid {
    books : Composition of many Books
                on books.publisher = $self;
}
```

## Create HTTP Request
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
