# Project Proposal

## Overview of the Project

The proposed system is an automated inventory management of computer labs.  The system should be will enough to be used in IoT labs and computer labs as well as to be used in any organization. A role based access control is to be enforced in order to define separate functionalities for different roles. A mobile app will be integrated to the system in order to make the system more user friendly and usable to both students and the staff. System will record inventory transaction events through web portal and mobile app, and will output inventory details, statistics and reports. The system will communicate with lecturers through auto-generated emails in order to make the system more accessible for them.

## Objectives of the Project

- Ensure that the items in the inventory are tracked and automate the process of borrowing of items from the lab.
- Handle any inventory changes including adding new items, modification of items etc.
- Ensure that the lab management and the item borrowing is done by only permitted individuals.

## The Need for the Project

Inventory management needs a lot of documentation, forms and folders when implemented manually. There is a need for automating inventory management in order to ensure the safety of the items in a laboratory, make borrowing of items efficient and make monitoring of labs simple for administrators. In current systems, users are required to do all the work manually which results in a lot of wasted time. Users being unable to see the availability of lab items also makes it harder for them. So a sustainable and reliable automated system is required in order to make this process more efficient and easy to use.

## Scope of the Project

The basic functionalities of the system are,

1. **Dynamically configurable role based access system.** Initially only the administrator and student roles will be available. Administrators can create new roles with different privileges and add accounts as staff. *Example: An administrator can create a role technical officer and grant privileges to create labs, add items, and lend items.*
2. **Registering students and staff into the system.** Registering will be done via an email sent to each student. Admin (or any user with relevant privileges) can add email addresses that are permitted to create accounts in the system.
3. **Requesting to borrow items in the lab by students.** Students can use mobile app to view and add lab equipment(App will show availability, etc...) and request to borrow them via a supervisor/lecturer. System will interact with supervisors/lecturers via emails in order to gain access on behalf of students. Students can then go to lab staff and borrow items.
4. **Lending the permitted items to the students by staff.** Through the mobile app, staff can easily scan item bar-codes and student ids to lend items.
5. **Creation of labs and assigning of staff into labs.**
6. **Maintaining the inventory of items of each lab.** Availability as well as other metrics can be easily monitored through the web application.
7. **Bar-code generation for items without serial numbers.**
8. **Marking items as damaged, unavailable and transferring items from one lab to another.**
9. **Utilize mobile app to use for entering item bar-codes and marking items.** Mobile app will directly support selecting items through the camera. Staff web app will be connected to each other in order to provide a seamless integration in order to increase user-friendliness.

## Deliverables

The main deliverables of the purposed system will be two separate **mobile applications** targeted for students and managing staff and a **web based application** for managing staff. Web application will be mainly focusing on desktops. The mobile applications will be made to be cross-platform with simplicity in mind. Mobile apps and web application will communicate with the **central server** using a **REST API**. The users will be able to access the **documentation** on a separate website.

- Students will not be able to sign in to the web application. All the student functionalities will be implemented in the mobile app.
- Staff members will be able to use both mobile app and the web app. Mobile app will mostly act as a helping tool for them.

## Overview of existing Systems

- **Inventory Management System for the Embedded lab** - Dept. of CSE
The current system is completely a manual system.  The records of items is in papers and borrowing of an item is done by filling a form.
- **ERPAG Inventory management software [1]** - This is a popular general inventory management software. This records inventory items but is more suited for warehouses. This is a subscription based online software.(starts at 49$ per month)

## Technologies we plan to use

Our proposal is to build a REST API using Node.JS and let the react web app and flutter mobile app communicate with the server. Mobile app will be cross platform and the web app will be targeting desktops.

- NodeJS (Backend) - [https://nodejs.org](https://nodejs.org)
- React (Web App) - [https://reactjs.org](https://reactjs.org)
- Flutter (Mobile App) - [https://flutter.dev](https://flutter.dev)

## References

[1] ERPAG. (2020). Inventory management software - ERPAG. [online] Available at: [https://www.erpag.com/inventory-management-software](https://www.erpag.com/inventory-management-software) [Accessed 2 Mar. 2020].
