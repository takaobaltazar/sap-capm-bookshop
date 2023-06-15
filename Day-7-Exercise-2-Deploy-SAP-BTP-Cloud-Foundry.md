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

### Steps: Configure Destination
1. **Right click** your root Fiori folder `(app/report)` > **Open Application Info**. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/2c346ed6-697f-4ddc-bd80-c84d53be68d0) </kbd>

2. Click **Add Deploy Config**.<br>   
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c8836a71-2827-4b24-9c28-79f8275f8bde)</kbd>

3. Fill-up required fields.
    - Target: **Cloud Foundry**
    - Destination Name: **Local CAP Project API (Instance Based Destination).**<br>   
    <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/50a85c48-46d4-4cf7-a923-b123b95147e0) </kbd>
    
4. After you configure the destination, the **mta.yaml** and **xs-app.json** file will be modified.
    - `xs-app.json`<br>   
    <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/d9b6964b-a891-4522-87d6-314c517d7971) </kbd><br>   
    
    - `mta.yaml`<br>   
    <kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/7cc2673e-cdd1-4ddb-ab87-2a2cdb2fd95e)</kbd>

5. This is to allow the Fiori Application to access the OData Service of NodeJS.

### Steps: Deploy to Production
1. Right click **mta.yaml** then click **Build MTA Project**.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/dfb58315-1bfe-4a9e-b943-896bfd9bd49b) </kbd>

2. Go to **mta_archives folder**. Right click the **.mtar file** > **Deploy MTA Archive.**<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8b695aba-bdbf-485e-b30d-1fb9569dac3b) </kbd>

3. A window will appear to login into Cloud Foundry. Please enter your **credentials** and click **Sign in**.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8249fcb5-c4ca-4a85-995a-82e1e30ec499) </kbd>

4. Enter the correct Cloud Foundry Endpoint.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/5da0646c-b2e4-42f5-8080-5a71d3c5f301) </kbd>

5. After you login, Set the **organization** and **dev space** by selecting from the dropdown.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/90f84c3f-2ec4-4073-a7cc-c634e339ba05) </kbd>

### Successful Deployment - UI and Node Service
1. **Fiori application** is deployed under **HTML5 Applications** residing in trial > HTML5 Applications.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/0417f0b9-58c1-43ba-bf30-19b69ee10fcc) </kbd>

2. **Node Service** is deployed under our **cloud foundry spaces**. It is residing in trial > Cloud Foundry > Spaces > dev > Applications. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/4c81a9fe-6fc2-4e76-a2c0-b949d42973c0) </kbd>



