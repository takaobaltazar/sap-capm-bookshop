# Day 8 Exercise 2 - External Service Remote
This is a reference of Code for Day 8 Exercise 2

## Create and Bind Destination
### Steps:
1. Open **terminal** and create **service key** for **destination**.
```cds
cf create-service-key zbootcamp-destination-service zbootcamp-destination-service-key
```
2. Bind your **destination service** using **cds bind**.
```cds
cds bind -2 zbootcamp-destination-service
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8c6561d1-064a-4126-8323-98d182bbb1d3) </kbd>

3. After you create **service key** and **bind** it, you should now be able to see it in SAP BTP under **trial** > **dev** > **Services** > **Instances**, under **zbootcamp-destination-service**.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/53a01c89-f8ac-40e6-9671-4728fd59f5d9) </kbd>

## Create and Bind XSUAA
### Steps:
1. Open **terminal** create **service key** for **xsuaa**
```cds
cf create-service-key zbootcamp-xsuaa-service zbootcamp-xsuaa-service-key
```
2. Bind your **xsuaa service** using **cds bind**.
```cds
cds bind -2 zbootcamp-xsuaa-service
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c2e02197-957d-44fd-ab0f-826df252d0d9) </kbd>

3. After you create **service key** and **bind** it, you should now be able to see it in SAP BTP under **trial** > **dev** > **Services** > **Instances**, under **zbootcamp-xsuaa-service**.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/756b2641-fb7f-40aa-b01b-c424457eb6f2) </kbd>

## Create / Import Destination
### Steps
1. Now, we will create / import the **North Wind** service into our **Destination** of SAP BTP. This allows us to connect from remote system within our BTP application.
2. Go to **trial** > **Connectivity** > **Destination** and **create** / **import** the **North Wind** destination. Copy below config and save it as **.txt extension** and import it as destination.
```
#
#Wed Jul 19 02:44:23 UTC 2023
Description=Northwind OData Service
Type=HTTP
HTML5.DynamicDestination=true
Authentication=NoAuthentication
WebIDEUsage=odata_gen
Name=NorthWind
WebIDEEnabled=true
ProxyType=Internet
URL=https\://services.odata.org
WebIDESystem=Northwind
```

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c5d2b191-9922-48e7-92c7-d01ec1551a6d) </kbd>

## Profile: Hybrid
### Steps:
1. Now, we will add a new **hybrid** profile. Open **package.json** file and include **[hybrid]** profile which contains the **NorthWind** service.
2. The profile name was name to **hybrid** since this was the generated in **.cdsrc-private.json** file, after we execute the **cds bind** command.
```json
"[hybrid]": {
    "NorthWind": {
        "kind": "odata-v2",
        "model": "srv/external/NorthWind",
        "credentials": {
            "destination": "NorthWind",
            "path": "/v2/northwind/northwind.svc/"
        }
    }
},
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/0a87982e-3a0f-449f-b3b1-337340b06b4e) </kbd>

## Profile: Production
### Steps:
1. Add **NorthWind** in production profile below **db** config.
```json
"NorthWind": {
    "kind": "odata",
    "model": "srv/external/NorthWind",
    "credentials": {
        "destination": "NorthWind",
        "path": "/v2/northwind/northwind.svc/"
    }
}
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1c053e21-ecdf-4cff-bd19-6c35fa02b139) </kbd>

## Install HTTP Client
### Steps:
1. Open **terminal** and Install **http-client module**
```
npm i @sap-cloud-sdk/http-client
```
2. In case you didn’t install the module and run your service, you will encounter this error.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/e28d848b-c570-4725-8107-a0b4cabfb0bf) </kbd>

## Run Service
### Steps:
1. Open **terminal** and run service using **cds watch --profile hybrid**

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/d1153078-daf9-441f-b518-046857f290ec) </kbd>

2. Select **Orders** under **/admin**. 

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/45a6110b-af91-4ea5-bec1-2487bc3445ce) </kbd>
