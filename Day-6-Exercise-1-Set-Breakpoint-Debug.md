# Day 6 Exercise 1
This is a reference of Code for Day 6 Exercise 1

## Set Breakpoint
### Steps
1. Open `admin-custom-service.js`.
2. Set `breakpoint` in `submitOrder` custom event by **clicking** beside the `line number`. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8dd6b283-6ed4-43b6-88e8-ba7fa97be99d) </kbd>

## Activate Debugging
### Steps
1. Click `Menu` > `Run` > `Start Debugging`.
2. This will start the application in `debug mode`.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/00a83041-a81e-4cfd-8710-e65d420c8b04) </kbd>

## Debug mode active
### Steps
1. `Debug mode` is now activated.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1dc22b3e-60d0-40bc-9697-6000c748218b) </kbd>

2. Debug View. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/77c89746-9ebe-4877-b1e5-88ffebbda86d) </kbd>

## Run existing HTTP Request
### Steps
1. Run your existing HTTP Request for POST `submitOrder`.
```http
### POST submitOrder - Custom event action
POST http://localhost:4004/admin/submitOrder
Content-Type: application/json

{
    "bookId": "3c013ac2-b1ae-461c-8ab0-2521d9f732b7",
    "quantity": 9
}
```

## Debugging Mode
### Description
After running an `HTTP Request`, and setting up breakpoint, you can now debug the code. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/db153fcf-348c-4d27-aed4-83b0e1b0288d) </kbd>

