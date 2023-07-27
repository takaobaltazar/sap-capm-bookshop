# Day 3 Exercise 1 - Field Validation
This is a reference of Code for Day 3 Exercise 1

## Add Access Control
### Steps:
1. Open **srv/admin-service.cds**
2. Add `@insertonly` before Books entity. 
```cds
@insertonly
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/27215341-3426-4844-8c7f-dca8222e90cf) </kbd>

## Add Input Validation
### Steps:
1. Open **db/domain-model.cds.**
2. Append `@mandatory` to `title` and `name` field.
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
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/b859bbfc-c5ad-4c57-8c86-212cbcaffe52) </kbd>

## Add New GET HTTP Request
### Steps:
1. Open **test/http/bookshop-request.http**
2. Add **GET HTTP Request** for **Books** entity, and put the request in end of the line.
```http
### GET Books
GET http://localhost:4004/admin/Books
Content-Type: application/json
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1f27afcf-f04d-43e9-9cfe-04905805957c) </kbd>

3. Click **Send Request**.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/6f2e2ed8-029f-4665-a999-4e8b9a78e8ef) </kbd>

## Add New POST HTTP Request
### Steps
1. Open **test/http/bookshop-request.http**
2. Add **POST HTTP Request** for **Books** entity, and put the request in end of the line.
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
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/9b1cd843-2958-4945-b1bc-8c39a75e4c04) </kbd>

3. Click **Send Request**.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/48c4c01e-1383-4a73-8007-a79f6cfb8927) </kbd>


