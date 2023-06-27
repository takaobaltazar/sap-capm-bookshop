# Day 8 Exercise 1 - External Service Local
This is a reference of Code for Day 8 Exercise 1

## Get Metadata of Northwind
### Steps
1. Open **North Wind** OData service using **$metadata**. Then save the xml data as **NorthWind.edmx**
     - https://services.odata.org/v4/northwind/northwind.svc/$metadata
       <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/f5391250-058c-4f72-abb0-499d32d153a0) </kbd>

## Import of EDXM
### Steps
1. Import the **NorthWind.edmx** file into your **root** folder of **zbootcamp**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/ce36de42-8aaa-46a6-a457-aff18a069a01) </kbd>

2. Import the **.edmx** file into our project using the `cds import command`.
```cds
cds import NorthWind.edmx
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/ba3dc2de-d6fb-40b4-8f2f-26412b6baea3) </kbd>

3. After executing **cds import**, the following are updated.
    - The **NorthWind.edmx** is imported to srv/external and is now remove from the root folder.
    - The **NorthWind.csn** file is generated based on the **.edmx** file.
    - The **package.json** file is updated with a **NorthWind** service.


## Include entity in Service Definition
### Steps
1. Open Service Definition **admin-service.cds** and include import of **NorthWind** service and entity **Orders**.
```js
using {NorthWind as external} from './external/NorthWind.csn';

(Please refer to screenshot below) ...

@readonly
entity Orders as projection on external.Orders {
    key OrderID, ShipName, ShipAddress, ShipCity, ShipCountry
}
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/7629f146-8c83-48c8-9f13-5cb6f2d389d6) <kbd><br>   

## Include New Endpoint in Service Implementation
1. Open Service Implementation **admin-custom-service.cds** and include custom logic **Orders**.
2. Also, in module.exports include **async**.
```js
module.exports = async function() {
    const { Orders } = this.entities;
    const NorthWind = await cds.connect.to('NorthWind');

    this.on(['READ'], Orders, async(req) => {
        const results = await NorthWind.run(SELECT.from(Orders));

        return results;
    });

    // Your previous code should go here.
}
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/0cde34d1-cfbb-47e6-8d2e-0ad6f07fd008) </kbd>

## Add Mock Data
### Steps
1. Create mock data for our external service which will run locally.
2. Under **srv/external**, create a folder **data** and create a file **NorthWind-Orders.csv** 
```csv
OrderID;ShipName;ShipAddress;ShipCity;ShipCountry
0;Ship 1;11 Street;QC;PH
1;Ship 2;12 Street;Manila;PH
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/7ccb591a-de82-4a00-b01d-a602e94edec5) </kbd>

## Include new profile
### Steps
1. Under **cds > requires**, add **local profile** to your existing **db sqlite**.
```cds
"[local]": {
    "db": {
        "kind": "sqlite",
        "credentials": {
            "database": "db.sqlite"
        }
    }
},
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/4dd3497b-6135-4255-8eeb-6fee927a7250) </kbd>


