# Day 3 Exercise 3 - Custom Event
This is a reference of Code for Day 3 Exercise 3

## Define Custom Event: Unbound Action
### Steps:
1. Open Service Definition **srv/admin-service.cds**
2. Define custom event **action** in Service Definition.
```cds
action submitOrder (bookId: String, quantity: Integer);
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c1cc7b06-41d7-4a26-b3a0-747c65d5253e) </kbd>

## Implementing Action
### Steps:
1. Open Service Implementation **srv/admin-custom-service.js**
2. Define custom event **unbound action** and name it to `submitOrder`. 
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
### Steps:
1. Open **bookshop-request.http**.
2. Add **POST HTTP Request** for `submitOrder`, and put the request in end of the line.
```http
### POST submitOrder - Custom event action
POST http://localhost:4004/admin/submitOrder
Content-Type: application/json

{
    "bookId": "3c013ac2-b1ae-461c-8ab0-2521d9f732b7",
    "quantity": 9
}
```

3. Click **Send Request**. These are the possible outcomes once you trigger the POST request. Try
    - Input **quantity** = 15, to trigger the error for **Order exceed stock. Available stock is: 10**.
    - Input **bookId** as emppty value, to trigger the error for **Book Id is mandatory**
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/4d250133-13ca-489a-b365-f695af1b3176) </kbd>



