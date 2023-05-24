# Day 3 Exercise 2
This is a reference of Code for Day 3 Exercise 2

## Create Service Implementation
Create a new file under `srv` folder and name it to `admin-service.js`

## Define Event Handler - ‘.after’
```js
module.exports = function() {
    this.after('READ', 'Books', (each, req) => {
        if (each.stock > 10) {
            each.title += " -- 10% off"
        }
    });
}
```

## Comment @insertonly
```cds
using {com.bookshop as bookshop} from '../db/domain-model';

service AdminService {
    // @insertonly
    entity Books   as projection on bookshop.Books;
    entity Authors as projection on bookshop.Authors;
    entity Publishers as projection on bookshop.Publishers;
}
```

## Add @impl
``` cds
using {com.bookshop as bookshop} from '../db/domain-model';

@impl: './admin-custom-service.js' 
service AdminService {
    // @insertonly
    entity Books   as projection on bookshop.Books;
    entity Authors as projection on bookshop.Authors;
    entity Publishers as projection on bookshop.Publishers;
}
```

## Rename Service Implementation
Rename the Service Implementation file from `admin-service.js` to `admin-custom-service.js`

## Define Event Handler - ‘.before’
```js
this.before('POST', 'Authors', async(req) => {
    const splitName = req.data.name.split(" ");
    const formattedName = splitName.map((item) => {
        return item.charAt(0).toUpperCase() + item.slice(1).toLowerCase();
    }).join(" ");

    req.data.name = formattedName;
});
```

## Add new HTTP Request
```http
### POST Authors
POST http://localhost:4004/admin/Authors
Content-Type: application/json

{
    "name": "jOhN dOe"
}
```




