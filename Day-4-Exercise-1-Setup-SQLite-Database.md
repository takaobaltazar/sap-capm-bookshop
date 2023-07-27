# Day 4 Exercise 1
This is a reference of Code for Day 4 Exercise 1

## Preparation of SQLite
### Deploy to SQLite
1. Open `Terminal` and execute command below.
```cds
cds deploy --to sqlite
```

2. The `package.json` will be modified to include the SQLite database

### Service running Persistent Database
1. Run the app using
```
cds watch
```
3. Service is now using the SQLite Database which will make data persistent.
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/47416c97-28a5-4c65-9694-e253fade08d3)</kbd>

## Setting up the SQL Tools
### Step 1: Setup SQL Tools
1. Click `SQLTools` from the left side menu.
2. Click `Add New Connection`.
3. Select `SQLite (Node)`.
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/3bd01825-03ea-4029-913e-6be48601f79e)</kbd>

### Step 2: Setup SQL Tools
1. Fill-up `mandatory fields` and click `Test Connection`.
  - Connection name: `Local SQLite Database`.
  - Database file: `/home/user/projects/zbootcamp/db.sqlite`.

> Note: Right click your `db.sqlite` and select `Copy relative path` to get the link of `Database file`. Alternatively, you can type `pwd` in terminal.

2. Click `Save Connection`.
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/31fe356d-3f6b-47f8-a611-f07839dc8bd8)</kbd>

### Step 3: Setup SQL Tools
1. Click `Connect Now`.  
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/c6784348-2ec1-4678-981e-05e7f72df66b)</kbd>

## Preview
1. The `Tables` and `Views` should now be available after you connect.
2. The `.sql` file allows you to execute query in `SQLite syntax`.
3. To run a query, click the **Run on active connection** above your SQL query. Alternatively, **right click** > **Run query**
![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1665aec4-5316-4a5e-a17d-1cf0013e51cf)
