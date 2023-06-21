# Day 7 Exercise 4 - Setup SAP BTP Work Zone
This is a reference of Code for Day 7 Exercise 4

## Setup Security
### Steps
1. Go to SAP BTP Cockpit and go to **trial** > **Security** > **Users** and click your `user / email`. It will open a window to display the details.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/adf925c5-d112-46a9-9442-fc6aa4502dec) </kbd> <br>   

2. Under **Role Collection tab**, click **Assign Role Collection** and select the following:
    - **Launchpad_Admin**
    - **Launchpad_Advanced_Training**
    - **Launchpad_External_User**
3. Click **Assign Role Collection**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/313a7e0b-e34c-4b04-90aa-b0ef4057e936) </kbd>

## Access Work Zone
1. Go to SAP BTP Cockpit and go to **Services** > **Instances and Subscription** > **SAP Build Work Zone, standard edition.**
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/4e3d7b85-1874-4982-94bd-7140c3130223) </kbd>

## Setup Site / FLP
### Steps
1. Click **Create Site**.               
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/cc932fd2-4aa0-4e1f-a7d6-998330ce75bf) </kbd>

2. Enter **Site Name** and click **Create**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/2f7be54c-9956-4613-a752-8b839a51871b) </kbd>

3. **Site / Launchpad** is now created. Click the `<` back button to go back in home menu.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/179dcfdd-52ea-41ff-bde8-9fd7a399a602) </kbd>

4. Go to **Content Manager** > **Content Explorer** and click the **HTML5 Apps**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/671b5e12-e619-4782-bfe5-e27d6be60883) </kbd>

5. Select the item **Bookshop Report** and click the **Add to My Content** button on the upper right screen.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/a3617cda-1e39-4e4d-92d9-3edd77906e28) </kbd>

6. Under **Content Manager**, go to **My Content**. You should now be able to see the **Bookshop Report** we added.

#### Create Catalog
7. Click **New** > **Catalog**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/0e3edad4-f752-42f9-9ffb-f737765c694c) </kbd>

8. Enter **Title** and **Description**.
    - Title: **Bookshop Catalog**
    - Description: **A Bookshop Catalog**
9. On the **Assignments** tab, click the **search input** to display list. Now, click the `+` button to add our Fiori App in **Catalog**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/39ecb6c2-cac5-4cac-bbf9-24cb03324bcd) </kbd>

10. Click **Save** and go back to **Content Manager**.

#### Create Group
11. Under **Content Manager**, go to **My Content**. You should now be able to see the **Bookshop Catalog** we created.
12. Click **New** > **Group**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/2da93321-b66c-46d0-963d-be6bf686007b) </kbd>

13. Enter **Title** and **Description**.
    - Title: **Bookshop Group**
    - Description: **A Bookshop Group**
14. On the **Assignments tab**, click the **search input** to display list. Now, click the `+` button to add our Fiori App in **Group**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/8e7cd2d5-bac6-401e-8fd7-4b0dc40c2e3e) </kbd>

15. Click **Save** and go back to **Content Manager**.

#### Setup Role
16. After we configure the **Catalog** and **Group**, we will setup the **role**.
17. For role, select **Everyone** from the table list. 
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/41c0826e-6cf6-4dca-bdc2-9ff3acb5de2b) </kbd>

18. Click **Edit**
19. On the **Assignments tab**, click the **search input** to display list. Now, click the `+` button to add our Fiori App in **Role**.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/dce3c796-5f31-4b46-b01e-d291e9101352) </kbd>

20. Click **Save** and go back to **Site Directory**.

### Access Site / FLP
1. Open **Bootcamp Launchpad** by clicking the **open new window** icon.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/91ce2738-05df-43f7-affa-222d84fb97ba) </kbd>

2. **Fiori Application** tile now available in Fiori Launchpad.
<kbd> ![image](https://github.com/takaobaltazar/sap-capm-bookshop/assets/9301953/5f473b89-92ad-4360-b1e8-a6580cd07dbe) </kbd>
