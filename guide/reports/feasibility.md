# Feasibility Report

## 1. Introduction

### 1.1 Overview of the Project

The proposed system is an automated inventory management of computer labs.  The system should be well enough to be used in IoT labs and computer labs as well as to be used in any organization. A role based access control is to be enforced in order to define separate functionalities for different roles. A mobile app will be integrated to the system in order to make the system more user friendly and usable to both students and the staff. System will record inventory transaction events through web portal and mobile app, and will output inventory details, statistics and reports. The system will communicate with lecturers through auto-generated emails in order to make the system more accessible for them.

This project will be an open-source, free software built for the target of letting users to manage university laboratories easily. Here any potential user will have to deploy the web app and the server in his/her own server and then let the users access the system. Mobile app will allow users to connect to the specific server.

In our project, we would create the base system and the required documentation site. We would host the system as a demonstration for the end users.

### 1.2 Objectives of the Project

- Ensure that the items in the inventory are tracked and automate the process of borrowing of items from the lab.
- Handle any inventory changes including adding new items, modification of items etc.
- Ensure that the lab management and the item borrowing is done by only permitted individuals.

### 1.3 The Need for the Project

Inventory management needs a lot of documentation, forms and folders when implemented manually. There is a need for automating inventory management in order to ensure the safety of the items in a laboratory, make borrowing of items efficient and make monitoring of labs simple for administrators. In current systems, users are required to do all the work manually which results in a lot of wasted time. Users being unable to see the availability of lab items also makes it harder for them. So a sustainable and reliable automated system is required in order to make this process more efficient and easy to use.

### 1.4 Overview of existing Systems and Technologies

- **Inventory Management System for the Embedded lab** - Dept. of CSE
The current system is completely a manual system.  The records of items is in papers and borrowing of an item is done by filling a form.
- **ERPAG Inventory management software [1]** - This is a popular general inventory management software. This records inventory items but is more suited for warehouses. This is a subscription based online software.(starts at 49$ per month)

### 1.5 Scope of the Project

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

### 1.6 Deliverables

The main deliverables of the purposed system will be two separate **mobile applications** targeted for students and managing staff and a **web based application** for managing staff. Web application will be mainly focusing on desktops. The mobile applications will be made to be cross-platform with simplicity in mind. Mobile apps and web application will communicate with the **central server** using a **REST API**. The users will be able to access the **documentation** on a separate website. Documentation will provide information on API details, how to deploy the system in their own server, etc...

- The base system will be created with extendibility in mind. Users who want to use the system in their own organizations will be able to easily change the necessary configurations and deploy in their own servers. The documentation would provide users the required direction.
- Students will not be able to sign in to the web application. All the student functionalities will be implemented in the mobile app.
- Staff members will be able to use both mobile app and the web app. Mobile app will mostly act as a helping tool for them.

## 2. Feasibility Study

### 2.1 Financial Feasibility

As mentioned in the overview, this project will be an open-source free software where the hosting and deploying the system has to be taken care by the lab administration. However for demonstration we will host and deploy the web server in a minimum viable manner.

#### Expenses

##### Web-app and database hosting

Since the proposed system is a centralized client-server application, web app hosting is a major cost. Here for the demo, we plan to use [Heroku](https://www.heroku.com/) in order to host the web app. To fulfill this purpose, Heroku [free plan](https://www.heroku.com/pricing) will be enough. This will also allow us to deploy the web app and Postgres database **without any cost** at the expense of limited performance and response time. Database will have a restriction on the number of rows in the free tier, but the this constraint will not matter much since this will be a demo website.

Documentation pages will be static. Thus, they will be served using [Github Pages](https://pages.github.com/). This will not result in any cost.

##### Multimedia hosting costs

We will use a separate CDN service(cloudinary) in order to deliver images in the demo. We will use the [free tier](https://cloudinary.com/pricing) in this service. Even though the free tier allows us to use only 25 credits\* monthly, because of the limited number of users and low usage of images, the required bandwidth will be very low. So we will not face any issues when using the **free plan**.

\*1 cloudinary credit = 1GB managed storage or 1GB net viewing bandwidth

When a user decides to use this system in their laboratory, he/she can change the system configurations to use their own CDN service easily. Since the scope of this system does not include many multimedia uses, the free tier would be enough to any user of this software.

##### Play Store/App Store deployment

> At the initial stage we will not target iOS deployment since the cost of creating an app store account is very high.

|Store|Cost|
|-|-|
|Play store(Android App)|25$ registration fee|
|App store(iOS App)|99$ annually|

We will initially publish the Android application to the play store. This app will be similar to that of the Moodle[9] app. The users(students/staff) can enter the server address and use the mobile app in their system.

This will be a cost on our side, but since it would be a one time payment, it wouldn't be a major issue.

#### Incomes

The system will follow the freeware software standards. **No cost will be charged from the potential customers**. Bug fixes and maintaining tasks will have an associated cost. At the initial stage potential market space will be the local universities.

Apart from the associated cost, there will be many benefits for the customers. Especially the extra effort that is associated with completing forms and keep records of equipment that is borrowed from the lab will be significantly reduced.

However, after initial deployment, we will not face any cost because the customers would have to host the application in their own environments.

### 2.2 Technical Feasibility

![Overview Topology](https://i.imgur.com/4e4nqMP.png)

#### Technology stack

This project is a client-server application based on multiple types of clients. Base technologies that this system will user are,

- **NodeJS** - Back-end
- **React** - Front-end web application
- **Flutter** - Front-end mobile application
- **Postgres** - Default Database system\*

*Even though postgres is supposed to be the default database, the system will be made to be database agnostic as possible.

#### Other important technologies

Back-end will use **JSON Web Tokens**[2] as the primary method of authentication. Also the system will have a **role based authentication**[3] system implemented from ground-up as to facilitate the requirements. For JWT verification, [jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken) package will be used.

Staff mobile app will have **barcode scanning** capabilities in order for the app to be used as a barcode reader. We plan to use [barcode scan](https://pub.dev/packages/barcode_scan) third-party library for this task.

In order to connect mobile app and the web app in real-time we will use **socket connections**[4]. For this feature we plan to use socket.io implementations on Node, React and Flutter. Here we will use a unique room for every user in order to share data between the same user's devices. Using this approach, we can let the user scan barcode in the mobile device and select items in the web app seamlessly.

**Automated Emails** will be sent through [node mailer](https://nodemailer.com/). Other automated tasks such as automatically checking for due date expired items, etc... will be done via **CRON jobs**[5] using [bull](https://www.npmjs.com/package/bull) package.

To **host user uploaded image content**(eg: item images/lab images) we will use [cloudinary](https://cloudinary.com/) CDN service. Even though cloudinary does not have a react integration SDK, we can use the existing JavaScript SDK to upload content into the network.[6]

To make the system easily usable, we will make the system as **database agnostic** as possible using the [sequelize](https://sequelize.org/) ORM[10] allowing the users to use any database of dialects: PostgreSQL, MySQL, MariaDB, SQLite and MSSQL.

#### Conclusion

According to the above resources and initial analysis, this project  is technically feasible.

### 2.3 Report and Time Feasibility

> This section describes specific hardware and software requirements / resources and time feasibility for the successful completion of the system development.

#### Report feasibility

> TODO

#### Time feasibility

> TODO

### 2.4 Risk Feasibility and Mitigation

In order to reduce system issues related to bugs, we will extensively test the system. Apart from that, following measures will be taken to mitigate other risks.

#### System fail

In case of a system fail, manual system should be continued. In that case, users should be able to continue the manual system as well as the automated system at the same time. For this specific requirement, our system will contain an additional item state. When an item is tracked under the manual system, staff can simply put that item under that specific state when the system restarts. Then that item will show up as unavailable to the students and the staff can reset the state when the item is reacquired.

#### Database Backups

Database backups will occur weekly(system administrators can change the frequency) in order to mitigate database failures.

#### Security issues

System will keep a log of every important action done by every user in order to make sure that tracking a user or an item is possible in case of some item going missing.

In order to authenticate users, the system will use an email based process, where users have to confirm account creation through an email sent to the email account given by the administrator. This will ensure that unauthenticated users will not be able to access the system. Apart from that, standard hashing and encryption methods will be used when storing user passwords and generating JSON web tokens.

### 2.5 Social/Legal Feasibility

#### Social Feasibility

The main users of the system are the students and the laboratory staff. A manual system would require both parties to go through a lengthy process for use-cases such as borrowing an item or adding an item to the inventory.
Most of these processes will be made much easy and reliable through the system. So the stakeholders will prefer this system over legacy manual systems.Yet constant user input during the development process and prior acknowledgement of users will ensure the user cooperation.
The technical know how of some users might be not adequate to use the system. In such a case users might have to be trained.

#### Legal Feasibility

##### Legal implications of the system

> TODO

##### Licensing

The core technologies used for the development of the system: React, Flutter, and Node are open-sourced under following licenses.

|Framework|License|
|-|-|
|NodeJs|[MIT License](https://github.com/nodejs/node/blob/master/LICENSE)|
|Flutter|[BSD 3-Clause "New" or "Revised" License](https://github.com/flutter/flutter/blob/master/LICENSE)|
|React|[MIT License](https://github.com/facebook/react/blob/master/LICENSE)|

Also, every library mentioned in this document uses MIT license. So they might not require any legal procedures for the use.

The system will be deployed as a free and open-source  software with MIT licensing to ensure  the intellectual property rights preservation and the ability for using for commercial license. So users will not have any legal issues to consider.

## 3. Considerations

- **Usability and Ease of use** - Users should be able to easily adapt and use the system. Even technologically challenged users must be able to easily understand and use the system. UI/UX should be simple and intuitive.
- **Maintainability & Flexibility** - System should be able to maintain for a long period of time and system should be able to adapt to any new design changes in the base system.
- **Security of the lab items** - Security should be high in the system since the entities involved are costly lab equipment. Something something....
- **Reliability** - System should not fail since that would disrupt a whole section of the university/organization that is using this system. Also there should be a fail safe mechanism in case the online system fails. (eg: manual system which can be later synced with the online system)
- **Clear and concise documentation** - Since this system is supposed to be extended by system users, clear documentation should be present.

Since this in not a system with neither a huge number of users nor a time critical application, performance is not an huge consideration. **However the system should be able to handle at least 250 concurrent users and the response time should not exceed 5 seconds.** This performance criteria will be taken into account when designing the system.

## 4. References

[1] ERPAG. (2020). Inventory management software - ERPAG. [online] Available at: [https://www.erpag.com/inventory-management-software](https://www.erpag.com/inventory-management-software) [Accessed 2 Mar. 2020].
