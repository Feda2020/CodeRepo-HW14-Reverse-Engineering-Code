# CodeRepo-HW14-Reverse-Engineering-Code

## Description

 This app allow users to use their email to create an account and log in then log out securely. The user’s data will be stored in MYSQL database. Passwords will be hashed for security. 

## Table of contents

* [Description](#Description)
* [Installation](#Installation)
* [User Story](#User-Story)
* [Application file walk through](#Application-file-walk-through)
* [Pictures](#Pictures)
* [Test](#Test)
* [Questions](#Questions)

## Installation

This app required the following dependencies: bcryptjs, mysql2, express, express-session, passport, passport-local, express-handlebars, sequelize.

## User-Story

As someone who wants to safely login to a website and create an account I need to know that my personal information is securely stored and I don't have to worry about getting my information exposed.

## Application-file-walk-through

### middleware

**isAuthenticated.js** js this file restricts user from visiting the website if not logged in. Then when the user login will continue to the restricted routs.

**config.json** this file provides connection configuration to connect to the server and its one of the boilerplate files.

**passport.js** in this file we are telling passport we are using local strategy which mean we want the login to be with a username or email and a password. This file direct the user to: 
*	Create an account if they don't have one.
*	Warn the user when using incorrect email.
*	Warn the user when using incorrect password.
***
## models

**index.js** this boilerplate file connects to database and imports the user’s login data. 

**user.js** require 'bcrypt for password hashing. This makes the database secure even if it gets compromised because it is an irreversible way to hide passwords, once hashed it can't be unhashed. We also have the following:
* Custom method that compares the unhashed password the user entered with the hashed password stored in our database. 
* We also have Hooks that will automatically hash the user's password before a user is created. 
***
## public/ js
**login.js** this file: 
* Get reference to our form and inputs.
*	Validate the user's email and password are entered.
*	Clear the form after the email and password run the loginUser
*	Then loginUser will do a post to our "api/login" if successful, it will redirect user to members' page.
*	Through an error if there is an error in the user's login.

**members.js** this file does a get request to figure out which user is logged in.

**signup.js** this file gets the reference to our database so:
* When a user sign up it validates that username and password are not blank.
*	If we have the username and password then run the signUpuser function.
*	Posts to the signup route and if successful will redirect to the members page
*	If there is an error throw an error alert
***
## stylesheets
**style.css** Styles how the application looks like **login.html**, **members.js**, **signup.html** are the html files that ensures the proper formatting of the texts and forms for the browser. 
***
## routes
**api-routes.js** this file contains: 
*	Route for signing in, if user has valid login information will be send to the members page.
*	Route for signup a user, our squelize user models configured to automatically hash the user's password. If done successfully it will proceed to log in the user, otherwise it will alert the user of an error.
*	Route for logging in the user.
*	Route getting user’s specific data to be displayed on the client side.

**html-routes.js** require path so we can use relative routs to our html. This file require:
* Our custom middleware to check if the user logged in
*	Check if the user already has an account, then send them to members' page.
*	Users who are not logged in will be redirected to the signup page.
***
## .env
Allow us to customize our individual environment variable to hide our database password.
***
**package.json** contains all package info, node modules used, version info etc

**server.js** this file: 
*	Requires the necessary npm packages.
*	Requiring the passport as we configured it.
*	Setting up PORT and require models for syncing.
*	Creates express app and configure middleware needed for authentication.
*	Uses sessions to keep track of our user's login.
*	Requiring our routs.
*	Syncing our database and logging in a message for the user when successful. 
***
 ## Pictures

![Application walk throw](/public/assets/appWalkThrow.gif)
***
![Signup](/public/assets/Signup.PNG)
***
![Log In](/public/assets/Login.PNG)
***
![Member's Page](/public/assets/Member-page.PNG)

## Test

Run node test and opened the application on the localhost then checked to make sure it was working locally.

## Questions
In case of any additional questions please visit my GitHub link: [Feda2020](https://github.com/Feda2020) 
Or don't hesitate to contact me via email: fido311@gmail.com
    