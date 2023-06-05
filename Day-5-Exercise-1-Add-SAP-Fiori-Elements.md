# Day 5 Exercise 1
This is a reference of Code for Day 5 Exercise 1

## Add SAP Fiori Project
### Steps
1. In `BAS`, open command palette (`Shift + Command + P for MAC` / `Ctrl + Shift + P for WIN`). Choose `Fiori: Open Application Generator`.<br>  
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/99dabfec-14e3-4cfb-a78a-9040abe55a37)</kbd>

2. Alternatively, from Get Started Page. Choose `Start from Template` > `SAP Fiori Application`.<br>   
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/e987c934-e2fe-404d-ad33-b485229294a1) </kbd>

## Template Selection
### Step
1. Select `SAP Fiori` > `List Report Page` from Application Type. Click **Next**.<br>  
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/7afa4244-977d-4dc4-bcaa-6fb6d2669fcf)</kbd>

## Data Source and Service Selection
### Step
1. Fill-up the following fields to define the data source, which will use the existing CAP Project. Click **Next**.
    - Data source: **Use a Local CAP Project**
    - Choose your CAP project: **zbootcamp**
    - OData service: **AdminService (Node.js)**

<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/9dde0ed9-ac04-4dc9-9e8a-b43ce70cf911)</kbd>

## Entity Selection
### Step
1. Select the entity `Books` as our main entity and click **Next**. <br>    
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/49637bfc-31c5-4be4-91fa-4e5caa6828bb) </kbd>

## Project Attributes
### Step
1. Fill-up the following fields to define project attributes and click **Next**.
    - Module name: **report**
    - Application title: **Bookshop Report**
    - Application namespace: **com.ui.bookshop**
    - Description: **A Fori application for Bookshop**
    - Minimum SAPUI5 version: **1.114.0**
    - Add deployment configuration to MTA project: **Yes**
    - Add FLP configuration: **No**
    - Configure advanced options: **No**

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/5b7ed7c9-5a99-407f-a302-01569a40938a) </kbd>

## Deployment Configuration
### Step
1. Fill-up the following fields to define the deployment configuration. Click **Finish**.
    - Please choose the target: **Cloud Foundry**
    - Destination name: **None**
 
 <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/3e555af1-fb29-4f66-a972-d209bcd7b54c) </kbd>
 
 ## Summary of Generated Fiori Project
 <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/12579a37-ad41-438a-bd35-5080d3c161f9) </kbd>
 
 ## Project Structure
 ### Explanation
 The generated Fiori App is created under `/app` folder of `CAP service`.
 <kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8d8d23bc-0bcc-443c-a1dd-f0feee87a05c)</kbd>

## Run your project
### Steps
1. Open terminal and run.
```cds
cds watch
```
2. Select the link inside Web Application.<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/b7674d8c-9e3c-4669-835d-58d21db45d7e) </kbd>
> The Fiori App is now recognized by the service.<br>   
> The Fiori Preview will launch Fiori App to check the annotation of each entity.
> Use only for development purposes.

3. Preview App<br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/708bef10-7769-48ad-9a09-5ecf9854744d) </kbd>

4. Click **Go** button to preview the data. <br>   
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/215aab00-5837-4953-8200-661d9a894456) </kbd>

