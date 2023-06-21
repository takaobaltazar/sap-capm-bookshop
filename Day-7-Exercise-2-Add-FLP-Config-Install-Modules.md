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
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/0c70e832-e85e-4a1c-84c9-60e16e5fc16f) </kbd> <br>   

## Install Modules
### Steps
1. Open again **terminal** and execute the command below:
```cds
npm i @sap/xssec
npm i passport
```

## Re-deploy application to SAP BTP
### Steps
1. Right click **mta.yaml** then click **Build MTA Project**.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/104704f2-f553-4c8a-933a-3a9b04c4ebbb) </kbd><br>   

2. Go to `mta_archives` folder. Right click the **.mtar file** > **Deploy MTA Archive**.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/fbf7f3b8-0281-4252-a6f7-762300f076f3) </kbd><br>   

3. A window will appear to login into **Cloud Foundry**. Please enter your **credentials** and click **Sign in**.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8249fcb5-c4ca-4a85-995a-82e1e30ec499) </kbd><br>   

4. Enter the correct Cloud Foundry Endpoint.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/5da0646c-b2e4-42f5-8080-5a71d3c5f301) </kbd>

5. After you login, Set the **organization** and **dev space** by selecting from the dropdown.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/90f84c3f-2ec4-4073-a7cc-c634e339ba05) </kbd>
