# Day 5 Exercise 2
This is a reference of Code for Day 5 Exercise 2

## Add annotation for Selection Fields
### Steps
1. Open **annotation.cds** in `app` > `report` folder path. 
2. Add annotations to service `Books`.
```cds
annotate service.Books with @(
    UI.SelectionFields: [title, stock, price]
);
```

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a9354357-8d59-47c4-9114-28da540f53b6) </kbd>
> The `SelectionFields` annotation will include filter bar.

<br>   

## Preview App with Selection Fields
### Steps
1. The `Filter Bar` will be displayed to allow filtering of data in table. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1ad493b5-dbd9-454e-b2a9-0ffc1c339ec5) </kbd>

## Enable Draft
### Steps
1. Open `admin-service.cds`.
2. Enable Draft to `Books` entity by adding `annotation` to Service Definition.
```cds
@odata.draft.enabled
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/284f2e68-491f-42e8-99d0-3f9468778a3e) </kbd>

3. Next is to `re-build` our local database. Execute the command below in `terminal`.
```cds
cds build
cds deploy –to sqlite
```

## Enable Draft : Create and Delete
### Steps
1. **Create** and **Delete** button is enabled to create entry for `Books` entity.
2. Click **Create** button. <br>  
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/101e2dc5-2c5d-4f60-944b-0ecb8632e2e8) </kbd>

## Enable Draft: Create Entry
### Steps
1. Fill-up required fields. An Indicator `Draft updated` once you start to fill-up the forms.
    - title: **Books Draft Testing**
    - stock: **450**
    - price: **1000**
3. Click **Create.** <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/3e7e7160-8f94-4760-a029-8456f8047012) </kbd>

## Enable Draft: Entry Created
### Steps
1. Once entry is submitted, the record will be displayed. You can click **Edit** in case you want to edit the record.
2. Go back to home using **browser back button**.<br>    
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/99b98763-a653-49f7-9601-c1b12eadd4ff) </kbd>

## Enable Draft: View created entry
### Description
1. Entry updated with new record. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1a147e18-5696-418f-b16a-f59497831b60) </kbd>

## Database record updated
### Description
1. New record is created in local database. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/6c951429-4aaf-4b64-8b09-022af51aba2c) </kbd>
