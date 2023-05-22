# Day 2 Exercise 1
This is a reference of Code for Day 2 Exercise 1.

## Use Projection in Service Definition
```cds
using {com.bookshop as bookshop} from '../db/domain-model';

service AdminService {
    entity Books   as projection on bookshop.Books;
    entity Authors as projection on bookshop.Authors;
}
```
