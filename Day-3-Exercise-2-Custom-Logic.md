# Day 3 Exercise 2 - Custom Logic
This is a reference of Code for Day 3 Exercise 2

## Create Service Implementation - Define Event Handler - ‘.after’
### Steps:
1. Define a service implementation by creating a file **admin-service.js** in **srv** folder.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/4615afe7-8fad-4093-b834-df08a4d26fd8) </kbd>

2. Open Service Implementation **admin-service.js**
3. Define a custom event handler **this.after**.
```js
module.exports = function() {
    this.after('READ', 'Books', (each, req) => {
        if (each.stock > 10) {
            each.title += " -- 10% off"
        }
    });
}
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/cd649807-3ed5-404a-9688-3f707f2c744e) </kbd>

## Modify Service Definition
Comment **@insertonly**
### Steps:
1. Open Service definition **admin-service.cds**.
2. Comment the code for `@insertonly` to allow us in executing other HTTP request for **Books** entity.  
```cds
// @insertonly
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a1b38716-fbec-45fe-ad4e-eccc832791dd) </kbd>

## Run Service
### Steps:
1. Open **terminal** and run `cds watch`.
2. Default service implementation will be used for the **same file name** with Service Definition.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/bfe0e019-4edd-4c20-8b6d-11faa6106eed) </kbd>

3. Query / Access the service using path **/admin/Books.**
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/07fd8804-d593-4da4-9ef2-e3f8ae9e377a) </kbd>

## Add @impl
### Steps:
1. Add annotation **@impl**.
``` cds
@impl: './admin-custom-service.js' 
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a8106d9f-510f-4cec-9133-9d92c648106d) </kbd>

## Rename Service Implementation
### Steps:
1. Rename the Service Implementation file from **admin-service.js** to **admin-custom-service.js**
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8fa44b1c-fcd2-4176-a527-ecb26c801623) </kbd>

2. Open **terminal** and run `cds watch`.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/852a3715-b706-4b6c-8935-2a0cdbe14796) </kbd>

3. Service Implementation still works using **@impl** annotation.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/bdace86a-7f27-41a6-8846-39a0fa7f945a) </kbd>

## Modify Service Implementation - Define Event Handler - ‘.before’
### Steps:
1. Open Service Implementation **admin-custom-service.js**
2. Define a custom event handler **this.before**.
```js
this.before('POST', 'Authors', async(req) => {
    const splitName = req.data.name.split(" ");
    const formattedName = splitName.map((item) => {
        return item.charAt(0).toUpperCase() + item.slice(1).toLowerCase();
    }).join(" ");

    req.data.name = formattedName;
});
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/62b6038d-4fa2-4f02-aed4-c51e39c14a89) </kbd>

## Add new HTTP Request
### Steps:
1. Open **bookshop-request.http**.
2. Add **POST HTTP Request** for **Authors** entity.
```http
### POST Authors
POST http://localhost:4004/admin/Authors
Content-Type: application/json

{
    "name": "jOhN dOe"
}
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/62d89d19-8229-4d14-928a-25f4fa7435c9) </kbd>

3. Click **Send Request**.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/b0bb795c-9b71-4f3c-ad45-8bd189702d89) </kbd>






