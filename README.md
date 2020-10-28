# CodeRepo-HW14-Reverse-Engineering-Code

## Description

 This app allow users to use their email to create an account and log in then log out securely. The users data will be stored in MYSQL database. Passwords will be hashed for securety. 

## Table of contents

* [Description](#Description)
* [Installation](#Installation)
* [User Story](#User-Story)
* [Application file walk through](#Application-file-walk-through)
* [Pictures](#Pictures)
* [Test](#Test)
* [Questions](#Questions)

## Installation

  This app required the following dependincies: bcruptjs, mysql2, express, express-session, passport, passport-local, express-handlebars, sequelize. 

## User-Story

  As someone who wantes to safely login a website and create an account I need to know that my personal information is securely stored and I don't have to worry about getting my information exposed.

## Application-file-walk-through

### middleware

**isAuthenticated.js** This file restricts user from visiting the website if not logged in. Then when the user logged in contiue to the restricted routs.

**config.json** This file provides connection configuration to connect to the server.

**passport.js** in this file we are telling passport we are using local strategy which mean we want the login to be with a username or email and a password. This file direct the user to: 
* Create and account if they don't have one. 
* Warn the user when using incorrect email.
* warn the user when using incorrect password.
***
## models

**index.js** the code in this file connects to database and imports the user login data. 

**user.js** require 'bcrypt for password hashing. This makes the database secure even if it gets compromised because it is an irreversable way to hide passwords, once hashed it can't be unhashed. We also have the following:
* Custom method that compares the unhashed password the user entered with the hashed password stored in our database. 
* We also have Hooks that will automatically has the user's password before a user is created. 
***
## public/ js
**login.js** This file: 
* Get referrence to our form and inputs
* Validate the user's email and password are entered
* Clear the form after the email and password run the loginUser
* Then loginUser will do a post to our "api/login" if succeccful, it will redirect user to members' page. 
* Code to through an error if there is an error in the user's login.

**members.js** this file does a get request to figure out which user is logged in.

**signup.js** This file gettign the regerence to our database to:
* When a user sign up it validates that username and password are not blank.
* if we have the username and passwork then run the signUpuser fuction.
* posts to the signup route and if successful will redirect to the members page
* if there is an error throw an error alert
***
## stylesheets
**style.css** Styles how the application looks like
**login.html**, **members.js**, **signup.html** are the pages' html the ensures the proper formatting of the texts and forms for the browser. 
***
## routes
**api-routes.js** This file contains: 
* Route for signing in, if user has valid login information will be send to the members page. 
* Route for signup a user, our squelize user models configured to automatically hash the user's password. If done successfully it will proceed to log in the user, otherwise it will show the user an error. 
* Route for logging in the user.
* Route getting users specific data to be displayed on the client side.

**html-routes.js** require path so we can use relative routs to our html. This file require:
* our custom middleware to check if the user logged in
* check if the user already has an account, then send them to members' page. 
* users who are not logged in will be redirected to the signup page. 
***
## .env
allow us to customize out individual environment variable.
***
**package.json** contains all package info, node modules used, version info etc

**server.js** This file: 
* require the necessary npm packages 
* requiring the passport as we configered it
* setting up PORT and require modles for syncing
* creates express app and configure middleware needed for authintication
* use sessions to keep track of our user's login.
* requiring our routs
* syncing out database and logging in a message for the used when successful.  
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
    