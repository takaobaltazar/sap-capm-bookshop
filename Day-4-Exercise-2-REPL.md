# Day 4 Exercise 2
This is a reference of Code for Day 4 Exercise 2

## Update package.json
### Steps
1. Open `package.json`
2. Add `model` section inside `cds > requires > db` before **"kind": "sqlite",**.
3. `Save` file.<br>  
```cds
"model": [
    "db",
    "srv"
],
```
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
1. After you enable the `REPL` using `cds repl`, connect to database.
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
await cds.run(SELECT.from('com.bookshop.Books').limit(2))
```
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1c4bac50-5e6b-4ea7-ab26-e66288420353)</kbd><br>  
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/1469ab87-cde0-4a91-96df-b6469d1bd81a)</kbd>

## INSERT
### Steps
1. Use `INSERT` query to create record from local database.
```cds
await cds.run(INSERT.into('com.bookshop.Books', { title: 'INSERT REPL'}))
```
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/55e505a7-8302-4a8f-a186-a098ac8ffd7e) </kbd><br>  
<kbd>![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/cc5f6afc-2c7a-447d-b527-7db8601d6d53) </kbd>

2. Local database modified for new record.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/75a2564c-9fae-441e-a24f-9aa500cd7125) </kbd>

## UPDATE
### Steps
1. Use `UPDATE` query to modify record from local database. Replace `<INSERT ID>` with ID of record.
```cds
await cds.run(UPDATE('com.bookshop.Books').with({stock: 10, price: 50}).where({ID: <INSERT ID>}))
```

2. Local database modified for updated record.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a2f46e60-2b99-4a3a-8820-c359756a61bd) </kbd>

## DELETE
### Steps
1. Use `DELETE` query to delete record from local database. Replace `<INSERT ID>` with ID of record
```cds
await cds.run(DELETE.from('com.bookshop.Books').where({ID: <INSERT ID>}))
```

2. Local database modified for deleted record.

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/b227e8cf-a8bf-47b0-965c-59313518a245) </kbd>
