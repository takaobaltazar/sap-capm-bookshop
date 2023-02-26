# Week 3 Exercises
This is a reference of Code for Week 3 Exercise.

## Table of Contents
1. [Week 3 Unit 1 Excercise](##week-3-unit-1-excercise)

## Week 3 Unit 1 Excercise

### Modify Service Definition
```cds
using { com.bookshop as bookshop } from '../db/domain-model';

service AdminService {
    entity Books as projection on bookshop.Books;
    entity Authors as projection on bookshop.Authors;
    entity Publishers as projection on bookshop.Publishers;
    
    action submitOrder (bookId: Books:ID, quantity: Integer);
}
```

### Add annotation for Selection Fields
```cds
annotate service.Books with @(
    UI.SelectionFields: [title, stock, price]
);
```
