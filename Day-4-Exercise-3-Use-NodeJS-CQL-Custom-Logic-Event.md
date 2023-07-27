# Day 4 Exercise 3
This is a reference of Code for Day 4 Exercise 3

## Enhanced **submitOrder** custom event
### Steps
1. Open `srv/admin-service.js` and modify the custom event `submitOrder`.
2. Modification includes using of `CQL`.
```cds
this.on('submitOrder', async (req) => {
    const { bookId, quantity } = req.data;
    const { Books } = cds.entities;
    const bookResponse = await SELECT.one(Books).where({ ID: bookId });
    if (!bookResponse) {
        req.reject(412, 'Book Id is invalid');
    }
    if (bookResponse.stock <= 0) {
        req.reject(412, 'Out of stock!');
    }
    if (quantity > bookResponse.stock) {
        req.reject(412, `Order exceed stock. Available stock is: ${bookResponse.stock}`);
    }
    return await UPDATE(Books, bookId).set({
        stock: bookResponse.stock - quantity
    });
});
```

## Comparison of UPDATE statement 
### As Single Expression like SQL statement.
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/6d1a03ea-a86d-427a-8696-f17525016735) </kbd><br>   

### As Object using Reflection Definition. (Recommended)
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8bec5fef-686f-4178-b74d-10a09b48693a) </kbd>

## Add new POST HTTP Request
### Steps
1. Open `bookshop-request.http`.
2. Add `POST HTTP` Request for `Books` entity, and put the request in end of the line.
3. Click `Send Request`.

```http
### POST Books
POST http://localhost:4004/admin/submitOrder
Content-Type: application/json

{
    "bookId": "100",
    "quantity": 9
}
```

## Response from HTTP Request
### Success Response
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/9db3ef6d-c327-48cc-b6aa-a554bbe8bf2f) </kbd>

### Error Response
To achive this error, kindly send again a **POST Request**
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/3a1642df-8ce1-4f4d-a203-a120289eba69) </kbd>

## Database record updated
1. After executing `HTTP request`, the local database should be updated.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/fa6b215a-fc2e-49b0-b85a-00d2a27da753) </kbd>
