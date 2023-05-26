# Day 3 Exercise 1
This is a reference of Code for Day 3 Exercise 1

## Add Access Control
```cds
using {com.bookshop as bookshop} from '../db/domain-model';

service AdminService {
    @insertonly
    entity Books   as projection on bookshop.Books;
    entity Authors as projection on bookshop.Authors;
    entity Publishers as projection on bookshop.Publishers;
}
```

## Add Input Validation
```cds
namespace com.bookshop;

using {
    managed,
    cuid
} from '@sap/cds/common';

aspect additionalInfo {
    name : String(120) @mandatory;
}

entity Books : managed, cuid {
    title     : String(100) @mandatory;
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

## Add NEW GET HTTP Request
```http
### GET Books
GET http://localhost:4004/admin/Books
Content-Type: application/json
```

## Add New POST HTTP Request
```http
### POST Books with title empty
POST http://localhost:4004/admin/Books
Content-Type: application/json

{
    "title": "",
    "stock": 100,
    "price": 550.00
}
```
