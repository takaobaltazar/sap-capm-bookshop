# Day 2 Exercise 3 - Common Aspects
This is a reference of Code for Day 2 Exercise 3

## Import Common Aspects
### Steps
1. Open `db/domain-model.cds`
2. Import the common aspect **managed** and **cuid** for all entities. 
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
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/791ec141-f012-489a-8cc6-5ab0ba1dddb5) </kbd>

## Check Metadata
### Steps
1. Open **terminal** and run `cds watch`.
2. Access the service and click the **/admin/$metadata**
    <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/45ca6305-c22d-40e7-9e45-6096220098ee) </kbd>


## Create HTTP Request
### Steps
1. Create **test/HTTP** folder in your root workspace.
2. Create HTTP request with file name **bookshop-request.http** and put under **HTTP** folder.
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
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/b973f8cb-150e-408e-8688-29bf2c8497f2) </kbd>

3. Click **Send Request** above your **POST <Link>**. Alternatively, you can do **right click** > **Send Request**

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/baa78f45-c079-4822-ac67-0223af84e8b3) </kbd>
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c8f1851a-4d72-4111-820d-fb9127813e6d) </kbd>
