# Week 1 Exercises
This is a reference of Code for Week 1 Exercise.

## Week 1 Unit 3 Excercise

### Define Data Model
```cds
namespace com.bookshop;

entity Books {
    key ID  : Integer;
    title   : String(100);
    stock   : Integer;
    price   : Decimal(9,2);
}

entity Authors {
    key ID  : Integer;
    name    : String(100);
}
```

### Define Services
```cds
using { com.bookshop as bookshop } from '../db/domain-model';

service AdminService {
    entity Books as SELECT from bookshop.Books;
    entity Authors as SELECT from bookshop.Authors;
}      
```

### Add Initial Data to Database

Authors:
```csv
ID,name
200,Scott Fitzgerald
201,Ralph Ellison
202,Virginia Woolf
203,Miguel de Cervantes
204,Ernest Hemingway
```

Books:
```csv
ID,title,stock,price
100,The Great Gatsby,10,500
101,Invisible Man,50,400
102,To the Lighthouse,5,385
103,Don Quixote,2,600
104,The Sun Also Rises,100,300
```
