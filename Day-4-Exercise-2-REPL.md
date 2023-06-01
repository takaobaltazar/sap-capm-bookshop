# Day 4 Exercise 2
This is a reference of Code for Day 4 Exercise 2

## Update package.json
### Steps
1. Open `package.json`
2. Add `model` section inside `cds > requires > db`.
3. `Save` file.<br>  
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a8c54b4a-b19f-4e26-a030-d864a94ebbca)</kbd>

## Enable REPL
### Steps
1. Open `terminal`.
2. Enter command in `terminal`.
```cds
cds repl
```
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/b53e5248-695e-49bd-915e-9929aa56d489)</kbd>

## Connect to Data Source / Database
### Steps
1. After you enable the `REP`L using `cds repl`, connect to database.
2. Enter command in `terminal`
```cds
await cds.connect.to('db')
```
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a8d051be-a1a1-4003-b2f7-ce77057367e5)</kbd><br>

3. Check `entities` of Table. Enter command in `terminal`.

## SELECT
### Steps
1. Use `SELECT` query to get records from local database.
```cds
await cds.run(INSERT.into('com.bookshop.Books', { title: 'INSERT REPL'}))
```
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1c4bac50-5e6b-4ea7-ab26-e66288420353)</kbd><br>  
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1469ab87-cde0-4a91-96df-b6469d1bd81a)</kbd>
