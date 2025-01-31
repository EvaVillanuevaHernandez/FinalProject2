<h1 align="center"> Medical Prescriptions</h1>

## Tabla de contenidos:
---

- [Description and context](#Description-and-context).
- [Installation guide](#installation-guide).
- [Data model](#data-model).
- [Postman](#postman).
- [User requirements](#user-requirements).
- [Use Cases](#use-cases).
- [First design](#first-design).
- [Usability and accessibility](#usability-and-accessibility).
- [Tech stack](#tech-stack).
- [Technology comparison](#technology-comparison).
- [Planning](#planning).
- [Conclusion](#conclusion).
- [Links](#links).
- [Author](#author).

## Description and context

### Where does this need come from?

Although we do not believe it, today there are still small medical practices that do not have a digitized patient management system, which is why there is a need for a simple application to store said information.

With this app we can provide a faster, more accurate and secure method of storing and accessing medical history. In addition, we are facilitating the work of doctors by allowing them to create prescriptions digitally and link them to patients, thus having a more efficient control of prescribed drugs.

In short, this application can help doctors to provide more efficient and high-quality care to patients, as well as make their work easier.

---
## Installation guide :rocket:

###### Requirements

- Eclipse IDE o IntelliJ IDEA.
- MySQL Workbench, to host the database also included in the project.
- PostMan, for RESTFul tests.
- Visual Studio Code.

###### First Steps 

- If you have already downloaded repositories from GitHub, download this repository.

https://github.com/EvaVillanuevaHernandez/MedicalPrescriptions.git

If you are new, follow these steps to be able to install the application.
:arrow_down: :arrow_down: :arrow_down:

###### Frontend

To get started, create an empty folder on your computer and open your Visual Studio Code.

Once open, go to Files > Open Folder > and select the folder you just created.

Cool! Now open a terminal in the new folder.

![image](https://user-images.githubusercontent.com/95490721/206923001-02dca638-9c1d-4b65-a5ca-f622c899171b.png)

Once you are in the terminal of your folder execute the following commands:

```
 _$git init_
 ```
 
```
 _$ git clone https://github.com/EvaVillanuevaHernandez/MedicalPrescriptions.git_
```

Install the dependencies and run the app locally:

```
_$ npm install_
```

There is still a bit to start using the application, now we must configure the backend.

###### Backend
 
To get started, open the backend of the project with the IDE of your choice.

![image](https://user-images.githubusercontent.com/95490721/206922111-cc3cae87-53f0-4a4e-b1e3-d304c016cf65.png)

Once you have the backend open go to MYSQL Workbench and create a DB with the name you prefer:

![image](https://user-images.githubusercontent.com/95490721/206922081-b979a949-b79d-40f7-96ce-0cbf6e28e5ad.png)

We are almost done, now you have to configure the properties of the applications with the data of your DB:

![aplications](https://user-images.githubusercontent.com/95490721/206922786-2debae45-be7d-4dbe-a88f-981c699fc96c.png)

 Once these steps are done, you can start your backend.

![image](https://user-images.githubusercontent.com/95490721/206922838-c909d359-0a04-4dac-994b-0e5004dd1bc9.png)

Don't forget to start the frontend too!!
 ``` 
 _$ cd frontend/_
 ```
 ```
 _$ npm start
 ```

---
## Data model

 - Entities and attributes.
 - Relations between tables.
 - Graph of the data model.

###### Entities and attributes

![ER](https://user-images.githubusercontent.com/95490721/205692474-f9b3c0d6-8830-48aa-9bd3-6412835facd4.png)

Here we can see the entity-relationship model from which we can deduct its keys, entities and relationships.

As we can see, we have a database with 5 entities that we will later transform into tables. These are:

+ Doctor: atributes:

  - ID: Identification number of each doctor (cannot be null).
  - Name: Name of the doctor.
  - Surname: First surname.
  - Second last name: Second last name.
  - Collegiate_Num: Collegiate number of each doctor.
  - User_ID: Foreign user key in the medical table. It relates the user to the doctor.
  - DNI: National identity document.
    
  - FK: USER_ID
  
+ Patient: patient attributes:

  - ID: Identification number of each patient (cannot be null).
  - Name: Name of the patient.
  - Surname: First surname of the patient.
  - Second_surname: Second surname of the patient.
  - Image: an image of the patient will be saved.
  - DNI: National identity document.
  - History: Medical history of each patient.
  
  - FK: DOCTOR_ID
  
+ Prescriptions: prescription information:
 
  - Posology: Medication dosage.
  - Date: Date of the recipe.
  - Patient_name: Name of the patient to whom the prescription is issued.
  - Doctor_name: Name of the doctor issuing the prescription.
  - ID: Recipe identifier number (Cannot be null).
  - Medicine: Name of the medicine that is issued.
  - Doctor_id: Identifier of the doctor who issued the prescription.
  - Patien_id: Identifier of the patient for whom the prescription is made.
  
  - FK:PATIENT_ID
  - FK:DOCTOR_ID
  
+ User: in this entity the user data will be stored:

  - ID: User identifier (Cannot be null).
  - Email: Email of the user.
  - Password: user password.
  - Username: Username.
  
+ Role: Roles in the application:
 
  - ID: role identifier number (cannot be null).
  - Name: Name of the role.
  
  The information in this table will not change.

+ User_Role:intermediate table that is generated by the N:N relationship between user and role.
  -FK:USER_ID
  -FK:ROLE_ID

###### Relationships between tables

  - USER-ROLE: Many-to-many relationship, many users can have many roles.
  - USER-DOCTOR: One to one relationship, the doctor is a user.
  - DOCTOR-PATIENT: One to many relationship, in my data model a patient is associated with a single doctor, since it is a private practice and the doctor is only interested in seeing the information of his patients.
  - DOCTOR- PRESCRIPTIONS: One to many relationship, a doctor can make many prescriptions.
  - PATIENTS- PRESCRIPTIONS: One to many relationship, a patient can have many prescriptions at the same time.

###### Data model graph

Relational Model:

![ModeloRelacion](https://user-images.githubusercontent.com/95490721/206920279-d4804fb8-1b43-4905-bfd6-f281d1c573e5.png)

 UML diagram:

![UML](https://user-images.githubusercontent.com/95490721/206920186-09be84cb-4711-401e-85fc-231f59735e04.png)

---
## Postman

https://documenter.getpostman.com/view/23478563/2s8YzZNeDX

---
## User requirements

###### Platform:
 - **P1** This app comes as a web app as it is understood to be made to be used in the workplace.
 - **P2** In any case, it can also be used on mobile or tablet devices since it is responsive.

###### Access:
 - **A1** The app has a guest screen that can be accessed without being logged in.
 - **A2** In order to use the page you must be registered as a doctor, an administrator will be in charge of registering the doctors previously.
 - **A3** To add, delete or modify the information of the doctors you must be an administrator.

###### Interfaces:

 - **I1** The app has 2 main interfaces that show lists of both patients and prescriptions.
 - **I2** The user registration and doctor registration interfaces will be available only for administrators.
 - **I3** In the main interfaces it will be possible to search patients by name.

###### Actions:

 - **A1** User actions will be accompanied by feedback and notifications.
 - **A2** When entering data in the form, it is validated that the information is entered correctly, notifying the user if there is an error.

###### Validations:

- **V1** When creating a prescription or patient users must enter the information correctly. 
- **V2** If this information is wrong, the user will receive an alert.


###### Reports:

- **R1** The user has the possibility to print the prescriptions of the patients.To do this, you only have to enter the data.
- **R2** You can also view history and a medication graph in the same way.

---
## Use cases.

Below we can see the use case diagram, this is reduced to the actions that the doctor (main user of the application) and the administrator (in charge of adding or removing doctors from the system) can perform.

![UseCaseDiagram1](https://user-images.githubusercontent.com/95490721/207313239-b5bb35f6-f40c-454c-b18f-7b6042d1e24b.jpg)

As we can see in the image, when consulting a prescription, the doctor can modify, update or delete it, the same can be done with his patients.

In the case of the administrator, its only function is to consult the doctors that are in the system, delete them, modify them or introduce new ones.

---
## First design

https://www.figma.com/file/7Qc0eVAa4K3pZEsE7mr6Jk/Centro--Artemisa?node-id=42%3A1680&t=uXte4oUDStnNrsMg-1

---
## Usability and accessibility :eyes:

###### Usability:
 
Regarding usability elements, we have a clear and simple clean design, adapted to all users. We recognize a color palette that is familiar to us from the medical field, but at the same time modern, including warmer colors.
 
 ![image](https://user-images.githubusercontent.com/95490721/206919510-3532a341-430c-4ce6-9c65-82e21cab3b7b.png)

 ![image](https://user-images.githubusercontent.com/95490721/206919497-a95362e0-3cf4-4acf-a469-a624acac2428.png)

 ![image](https://user-images.githubusercontent.com/95490721/206919999-6e7ff21b-3312-4766-83c4-27e6abe0409d.png)
 
 - Easy to understand, the user does not need more than three clicks to reach his goal with minimal effort. In addition, essential information is visible and clear.
 
 - Has clear icons and labels so that users can quickly identify the different sections and actions.
 
 - It integrates a predictive search system that displays results as you type search terms, making it easier to navigate and locate information.
 
 - Elegant in its design, it favors the user's perception, the soft colors of its interface and the homogeneity make the end user feel attracted to the product.
 
 - The user is able to interact with the application thanks to its elegant and simple design, overloading is avoided, which makes it difficult for users to easily navigate through applications.
 
 - Feedback and appropriate responses to user actions through messages and alerts
 
 - Clean layout of windows to create a seamless visual flow of information for the user.
 
 - Consistent interface, basic operations are intuitive and all done in the same way.
 
 - Clear and harmonious interface structure, menus and windows are consistent with each other.
 
 - Easy navigation through the page, both with mouse and keyboard.
 
 
######  Accessibility 
  
 - Accessibility is the attribute that allows people to easily perceive, understand and navigate the web. For this, the following has been taken into account:
 
 - Contrast between the background and the color of the font to favor reading and favor visual health, also pure white is not used to avoid glare and visual fatigue.
 
 - Compatible with assistive technologies, such as screen readers and alternative keyboards, so that users with disabilities can use it without any problems.
 
 - Well-defined form fields and fonts that favor the perfect legibility of the texts.
 
 - Design adaptable to all kinds of devices.

---
## Tech stack

* [Angular 15](https://angular.io/)
* [Node v16.14.2](https://nodejs.org/en/)
* [Spring Boot v2.5.7](https://spring.io/projects/spring-boot)
* [Hibernate](https://hibernate.org/)

---
## Comparison of technologies

For the comparison of technologies I have chosen the most similar and used ones. Angular vs React for the frontend and Node vs Springboot for the backend:

###### Main differences between Angular and React:

Architecture: Angular is an MVC (Model-View-Controller) architecture framework, while React uses a component-based architecture. In Angular, the developer defines models, views and controllers, while React uses a reusable component-based framework.

Learning curve: Angular has a steeper learning curve compared to React. Angular has a lot of concepts and terminology that developers need to learn, while React is easier to learn and use.

Integration with other tools: Angular has a number of additional tools, such as Angular CLI, which helps developers create Angular projects and generate code faster. React does not have a similar built-in tool, but it can easily integrate with other JavaScript tools, such as Babel and Webpack.

###### Main differences between Node and SpringBoot:

- Node.js, developed primarily in Javascript, uses a single-threaded, event-driven, non-blocking I/O model. This makes it incredibly efficient and lightweight. It is perfect for data-intensive applications that need to run in real time on distributed teams.

- Spring Boot allows you to get a productive application up and running quickly. The idea behind Spring Boot is that it is very easy to run, so it minimizes the amount of hassle involved in getting an application up and running.

Advantages of Node:

```
- Javascript community: Grows quickly.
- Lightweight, fast
- Single-threaded - low memory usage
- Excellent for I/O tasks
- Npm is constantly growing.
```
Advantages of Spring Boot:

```
- Java community: mature and thriving.
- Java is typed (checked at compile time).
- Long-term support and maintainability.
- Support for multiple threads.
- Ease of use of many dependencies.
```

###### Native, hybrid web and PWD applications:

**On the frontend**.

Both Angular and React can be used to develop hybrid mobile apps, web apps and PWA (Progressive Web Apps).

As for hybrid mobile apps, both frameworks allow you to create apps using tools like Cordova or Capacitor. However, there are some differences in how they integrate with these tools. In the case of Angular, Ionic is used as the framework for creating hybrid mobile apps, while in React, different tools such as React Native or NativeScript can be used. 

As for web applications, in my case, both Angular and React are a good choice. Angular provides a clear and defined project structure and many useful tools for web application development. React, on the other hand, offers flexibility and ease of use, which can be useful in small to medium-sized projects.

Finally, in terms of PWA, React is a good choice as it is designed to be used in progressive web apps. However, Angular is also a good option, as it offers tools for creating high-quality PWAs.

In summary, both Angular and React are viable options for developing hybrid native apps, web apps and PWAs. The choice of the best framework will depend on the specific project and the requirements of the development team. 

**In the backend

Regarding the backend, using Spring Boot with a programming language already known to me as Java, it was easier for me to adapt and learn to build a backend with this tool.


---
## Planning 📋

For this project we have used GitHub's projects tool, which allows you to organise and distribute tasks.


---
## Conclusion :bulb:

After working as a team on this project, we learned the importance of collaboration and communication to achieve our common goals. We used current technologies such as Angular, TypeScript, IndexDB and other web development tools to build a functional and scalable application. In addition, we have learned how to handle bugs and find creative solutions to solve technical problems. Overall, it has been a valuable and enriching experience that has allowed us to improve our technical and social skills.

---
## Links 📖

- https://www.w3schools.com/
- https://material.angular.io/components/icon/overview
- https://spring.io/projects/spring-boot
- https://docs.angular.lat/tutorial/toh-pt0
- [https://reactjs.org/docs/getting-started.html](https://ng.ant.design/docs/introduce/en)

## Author :woman_technologist:

- Eva Luna villanueva Hernández
- Juan Alberto Trujillo Carballo

---
