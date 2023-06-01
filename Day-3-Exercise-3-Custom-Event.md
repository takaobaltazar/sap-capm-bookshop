# Day 3 Exercise 3
This is a reference of Code for Day 3 Exercise 3

## Define Custom Event: Unbound Action
```cds
using {com.bookshop as bookshop} from '../db/domain-model';

@impl: './admin-custom-service.js' 
service AdminService {
    // @insertonly
    entity Books   as projection on bookshop.Books;
    entity Authors as projection on bookshop.Authors;
    entity Publishers as projection on bookshop.Publishers;

    action submitOrder (bookId: String, quantity: Integer);
}
```

## Implementing Action
```js
this.on('submitOrder', async (req) => {
    const { bookId, quantity } = req.data;

    if (!bookId) {
        req.reject(412, 'Book Id is mandatory');
    }
    if (quantity > 10) {
        req.reject(412, 'Order exceed stock. Available stock is: 10');
    }

    return bookId;
});
```

## Add new POST HTTP Request
```http
### POST submitOrder - Custom event action
POST http://localhost:4004/admin/submitOrder
Content-Type: application/json

{
    "bookId": "3c013ac2-b1ae-461c-8ab0-2521d9f732b7",
    "quantity": 9
}
```



