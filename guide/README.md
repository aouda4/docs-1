# User Manual

**The project is already deployed at [https://openinventoryorg.github.io/web-frontend/](https://openinventoryorg.github.io/web-frontend/)**. So ypu can test the system from this endpoint rather than configuring the project from scratch. If not follow the building from source guide to build the project from scratch.

After you run the project, you will receive an email( specified as admin email in `.env` file) with a link to the registration page .Then click the link and start your admin account registration by completing the form. After you completed the form hit the register button and you will be directed to the login page.

## Web application

### Administration Functionalities

Roles with Administrator permission can perform these following functionalities.

- Create new Role: Create a role with role name and granted permissions
- Manage Role: List roles with their permission,delete roles
- View Users: View currently active users in the system and their details
- Add Supervisors: Adding Supervisors to the system
- View Supervisors: View all supervisors in the system and their details

### Lab Management Functionalities

Roles with Lab Manager permission can perform these following functionalities.

- Create Laboratories: Create a lab with title, subtitle, and an image(optional)
- View Laboratories: View the labs in the system with details.
- Assign Staff Members: Assign staff members with lab manager permission to labs

### Item Management Functionalities

Roles with Inventory Manager and Lab Manager permissions can perform these following functionalities.

- Create Item Set: Create an item set with title, image (optional) and attribute name, value pairs. A non editable attribute should have a default value
- View Item Sets: View the itemsets in the system
- Create Item: Create an item with serial number, itemset and lab. Serial number can be scanned through the mobile app
- View Item: View the items in the system

### User Account Registration Functionality

Roles with Registrar permission can perform these following functionalities.

- Invite Users : Invite users to the system through their emails
- Retract invitation: Retract invitations that are sent
- Note that users with accepted invitations cannot be removed.

### Inventory Management Functionalities

Roles with Inventory Manager permission can perform these following functionalities.

- Lend Items : Select item to be lent in the list and scan serial number through mobile app,then lend the item
- Receive Items:
- Temporary Handover : Scan the serial number through mobile app and lend

## Mobile Application

You can login to the mobile app as a student or a staff user. Either way, you will have to enter the server URL at the start of the app. Use the URL specified in the ome page of the web frontend here. (eg: )

After that depending on your user type, you will be taken to the home page. As a staff user you can scan barcodes and temporary handover items. As a student you can request items.
