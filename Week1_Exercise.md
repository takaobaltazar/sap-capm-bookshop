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

### Adding Custom Logic - Event Handler 
```js
module.exports = function() {
    this.after('READ', 'Books', (each, req) => {
        if (each.stock > 10) {
            each.title += " -- 10% off"
        }
    });
}
```

### Define Custom Events: Action
```js
action submitOrder (bookId: Books:ID, quantity: Integer);
```

### Define Custom Events: Unbound Action
```js
this.on('submitOrder', async (req) => {
    const { bookId, quantity } = req.data;
    const { Books } = cds.entities;
    const bookResponse = await SELECT.one(Books).where({ ID: bookId });
    if (!bookResponse) {
        req.reject(412, 'Book Id is invalid');
    }
    if (bookResponse.stock <=0) {
        req.reject(412, 'Out of stock!');
    }
    if (quantity > bookResponse.stock ) {
        req.reject(412, `Order exceed stock. Available stock is: ${bookResponse.stock}`);
    }
    return await UPDATE (Books, bookId) .set({
        stock: bookResponse.stock - quantity
    });
});
```

### Define HTTP Request
```http
POST http://localhost:4004/admin/submitOrder
Content-Type: application/json

{
    "bookId": 100,
    "quantity": 9
}
```
