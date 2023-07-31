# Day 7 Exercise 3
This is a reference of Code for Day 7 Exercise 3

## Add FLP Config
### Steps
1. To support our app For Fiori Launchpad Service, we need to add an **FLP Config**.
2. Open **terminal** and execute the command below:
```cds
cd app/report
npx -p @sap/ux-ui5-tooling fiori add flp-config
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/0c70e832-e85e-4a1c-84c9-60e16e5fc16f) </kbd>

3. After executing the command to configure the FLP Config, the **manifest.json** file will be modified:
   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/6e962f01-b99d-41a2-ad5c-c5c9ad1e6189) </kbd>

## Re-deploy application to SAP BTP
### Steps
1. Right click **mta.yaml** then click **Build MTA Project**.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/104704f2-f553-4c8a-933a-3a9b04c4ebbb) </kbd><br>   

2. Go to `mta_archives` folder. Right click the **.mtar file** > **Deploy MTA Archive**.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/fbf7f3b8-0281-4252-a6f7-762300f076f3) </kbd><br>   
