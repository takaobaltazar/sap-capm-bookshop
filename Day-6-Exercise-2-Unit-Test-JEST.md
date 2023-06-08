# Day 6 Exercise 2
This is a reference of Code for Day 6 Exercise 2

## Create Test file
### Steps
1. Create file `admin-service.test.js` under `/test` folder.
```js
const path = require("path");
const cds = require("@sap/cds/lib");
cds.test(path.join(__dirname, ".."));

describe("Check Admin Service", () => {
    it("When Posting records for Books, it should return data", async () => {
        // Arrange
        const { Books } = cds.entities;
        const bookTitle = "Book Sample";

        // Act
        await cds.create(Books, {
            title: bookTitle
        });
        const [expectedResponse] = await cds.read(Books).where({title: bookTitle});

        // Assert
        expect(expectedResponse).toMatchObject({
            title: bookTitle,
            stock: null,
            price: null,
            author_ID: null,
            publisher_ID: null
        });
    });
});
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/60fe7b61-c59f-429a-9a23-136815521527) </kbd>

## Execute JEST
### Steps
1. Execute command to run JEST
```js
npx jest test/admin-service.test.js
```
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/9ff8f485-7e6a-43e0-b009-a69518859448) </kbd>

2. Result from JEST <br>    

<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/d6c14ec2-de0b-4e19-93f3-5787c20f746d) </kbd>
