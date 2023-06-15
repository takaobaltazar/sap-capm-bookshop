# Day 7 Exercise 2
This is a reference of Code for Day 7 Exercise 2

## Check HANA Database
### Steps
1. Ensure that **HANA Database** is up and running to avoid any issue during deployment.
2. Go to **trial** > **Cloud Foundry** > **Spaces** > **dev** > **SAP HANA Cloud**. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c4e6e1b9-9aa9-4a27-a24e-c602280a0a4b) </kbd>

3. Start the **database**. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8e5cf0a0-b99e-4481-bc9c-9435cecb70ff) </kbd>

## Prepare for Production
### Steps: Approuter
1. Open your project in SAP BTP and right click **mta.yaml** > **Create MTA Module from Template**.<br>   
2. Select **Approuter Configuration**.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/9e4e3995-aebd-4c5a-b57f-1f971b055657) </kbd>

3. Fill-up required fields for the Approuter Configuration. Click **Next**.
    - HTML5 application runtime: **Managed Approuter**
    - Unique name of project: **com.approuter.bootcamp**
    - Do you plan to add a UI? **Yes**<br>   
    <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/e481c810-6499-468b-8e20-b529f011ac88) </kbd>

4. It will now add approuter configuration to your **mta.yaml** file. Also, it will generate a new file **xs-security.json**<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/d091d382-2c44-4823-afcc-4feb3a2c5d0a) </kbd><br>    

### Steps: Add Hana
1. Open **terminal** and execute the command to add hana configuration. This is `one time setup only` together with the approuter configuration.
```cds
cds add hana --for production
```

2. The **package.json** will be modified and will include configuration for production database which is Hana Cloud. Also, the **yaml** file will be modified. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/cf9e3cb8-ee79-4e19-a25c-3447e7078023) </kbd>

### Steps: npm install
1. Open **terminal** and execute command below to install dependencies.
```cds
npm install
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a587a26c-0fa1-415b-ba85-2c33bcbc4d3c) </kbd>


