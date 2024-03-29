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
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/88549c46-6a92-470e-90f3-7c2a745a1777) </kbd>

4. Click **Finish.**    

## Preview of Initial Project Workspace
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c56d6017-1885-460a-bb0e-e6a81f9f6fab) </kbd>

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

## Run Service
Using **cds watch** to run the service.
### Steps:
1. Open **terminal** by clicking the **Menu (Burger Icon)** > **Terminal** > **New Terminal**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/db4dfe5d-3619-447e-a7a9-fd6ba726b694) </kbd>
                     
2. Run your project using below command
```cds
cds watch
```                 
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/14bde384-7668-4444-9cbc-8f1d628e9c5a) </kbd>

3. Click **Open in a New Tab** button to view the service. It will open a new browser tab to display list of service endpoints.<br>   


## Add Initial Data to Database
Create **data** folder under **db** root folder, to add Initial data. Use below file name format.   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/3c32c3d3-8629-48bf-b111-b34c9c097f38) </kbd><br>   

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

## Service running with Data
1. After you add initial data, your **cds watch** in terminal should restart to reflect the changes made in your file. In case you closed it, open again **terminal** and execute the **cds watch** command.
2. Data are now loaded into the database.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/18753a3d-2de1-4247-8ba2-bc69a6335c58) </kbd>

3. Query / Access the service using path /admin.
    - admin/Authors
    - admin/Books    
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/7872b628-e775-4622-984c-d3ac50d65902) </kbd>

