# Day 2 Exercise 2 - Aspect, Association and Composition
This is a reference of Code for Day 2 Exercise 2

## Define Aspect and New Entity
### Steps:
1. Open `db/domain-model.cds` file.
2. Create **name aspect** as **additionalInfo** and assigned it to entity.
3. Remove the **name** field in **Authors** entity.
4. Create new entity **Publishers.**
```cds
namespace com.bookshop;

aspect additionalInfo {
    name: String (120);
}

entity Books {
    key ID  : Integer;
    title   : String(100);
    stock   : Integer;
    price   : Decimal(9,2);
}

entity Authors: additionalInfo {
    key ID  : Integer;
}

entity Publishers: additionalInfo {
    key ID  : Integer;
}
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/218fc79e-784c-43a6-97bc-e811b9c1653e) </kbd>

## Add new Entity in Service Definition
### Steps:
1. Open `srv/admin-service.cds`
2. Include **Publisher** entity to Service Definition to expose the service.
```cds
entity Publishers as projection on bookshop.Publishers;
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a1d51e79-42f0-4316-832b-87b345d9e664) </kbd>

## Access and Check Metadata
### Steps:
1. Open **terminal** and run `cds watch`.
2. Access the service and click the **/admin/$metadata**
    <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/0c153169-03c2-4156-a391-76fd0f2f421e)</kbd> <br>   
    <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/42e17973-cd7a-48a4-80cf-d096d75a3ee4) </kbd>


## Add Association and Composition
### Steps:
1. Open `db/domain-model.cds`
2. Include relationship for each entity.
```cds
namespace com.bookshop;

aspect additionalInfo {
    name : String(120);
}

entity Books {
    key ID        : Integer;
        title     : String(100);
        stock     : Integer;
        price     : Decimal(9, 2);
        author    : Association to Authors;
        publisher : Association to Publishers;
}

entity Authors : additionalInfo {
    key ID    : Integer;
        books : Composition of many Books
                    on books.author = $self;
}

entity Publishers : additionalInfo {
    key ID    : Integer;
        books : Composition of many Books
                    on books.publisher = $self;
}
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/cf949fce-0459-47f5-a364-7b39c4a2c87b) </kbd>

## CDS Graphical Modeler
You can define entity using **CDS Graphical Modeler**.
It can be access by right click of **Model Definition** > **Opens With** > **CDS Graphical Modeler**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/0e3be667-126a-432b-be51-6e1bdddcdb66) </kbd>

## Add Initial Data to Publisher entity and Modify Data for Books entity.
Add initial data by creating file under **db/data**.   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1b43df54-682f-4109-810f-9372fea16ad6) </kbd>

### Steps:
1. **db/data/com.bookshop.Publishers.csv:**
```csv
ID;name
300;Charles Scribner's Son
301;Penguin Random House
302;The Hogarth Press
303;Blas de Robles
304;Charles Scribner's Sons
```

2. **db/data/com.bookshop.Books.csv:**
    - Modify data for Books entity. Include reference to **Publisher entity** by including **author_ID** and **publisher_ID**.<br>
```csv
ID;title;stock;price;author_ID;publisher_ID
100;The Great Gatsby;10;500;200;300
101;Invisible Man;50;400;201;301
102;To the Lighthouse;5;385;202;302
103;Don Quixote;2;600;203;303
104;The Sun Also Rises;100;300;204;304
```

## Run Service
### Steps
1. Open **terminal** and run `cds watch`.
2. Data are now loaded into the database.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c7d641de-9a1d-491f-84de-a327adf8f2f6) <kbd>
3. Query / Access the service using path **/admin**.
    - **admin/Publishers**
    - **admin/Publishers?$expand=books**
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/de10b91d-770a-4e40-a3fb-0d8d875e73c2) </kbd>

