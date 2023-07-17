# Day 1 Exercise 1 - Getting Started with CDS
This is a reference of Code for Day 1 Exercise.

## Create initial project via Wizard
### Steps:
1. Open your **Business Application Studio (BAS)** in **SAP BTP**.            
2. Click **Menu** > **File** > **New Project from Template** and select **CAP Project**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/af1c0b7d-f2cd-4184-8205-f20ddc9cbbb1) </kbd>

3. Fill-up CAP Project Details:
    - Project Name: **zbootcamp**
    - Runtime: **Node.js**
    - Include feature: **MTA based SAP Business Technology Platform Deployment**
4. Click **Finish.**                   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/88549c46-6a92-470e-90f3-7c2a745a1777) </kbd>

## Preview of Initial Project Workspace
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c56d6017-1885-460a-bb0e-e6a81f9f6fab) </kbd>

## Run Service
Using **cds watch** to run the service.
### Steps:
1. Open **terminal.**                     
2. Run your project using below command
```cds
cds watch
```                 
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/d92b8a5c-2d8b-4a76-8498-3a935a0a6b6c) </kbd>


## Define Data Model
### Steps:
1. Define **Domain models** by creating file name **domain-model.cds** in **db** folder.
2. Copy the following code below: 
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

## Define Services
### Steps:
1. Define **Services** by creating file name **admin-service.cds** in **srv** folder.
2. Copy the following code below.
```cds
using { com.bookshop as bookshop } from '../db/domain-model';

service AdminService {
    entity Books as SELECT from bookshop.Books;
    entity Authors as SELECT from bookshop.Authors;
}      
```

3. The **cds watch** reacted to the file change. In the log output, the service definition have been compiled.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/ed259e51-a41a-46b3-b484-0384e0d12852) </kbd>

## Add Initial Data to Database
Add Initial data by creating files under **db/data**. Use below file name format.
### Steps:
1. **db/data/com.bookshop.Authors.csv**:
```csv
ID,name
200,Scott Fitzgerald
201,Ralph Ellison
202,Virginia Woolf
203,Miguel de Cervantes
204,Ernest Hemingway
```

2. **db/data/com.bookshop.Books.csv**:
```csv
ID,title,stock,price
100,The Great Gatsby,10,500
101,Invisible Man,50,400
102,To the Lighthouse,5,385
103,Don Quixote,2,600
104,The Sun Also Rises,100,300
```
