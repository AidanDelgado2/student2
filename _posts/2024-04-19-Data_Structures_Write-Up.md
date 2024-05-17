---
toc: true
comments: true
layout: post
title: Data Structures Write-Up
type: hacks
courses: {'csp': {'week': 20}}
---

## Collections
# Unique collection/table in database display rows and columns in the table of the SQLite database. 
I used the database from our lebron project. It includes usernames, passwords, and date of births.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_1.png" height="400" width="1500">

### Unique code that was created to initialize table and create test data.
This code models the user database that is previously pictured, and also includes the passwords to each user that are hidden in the database table. It includes every portion of data, with the name, username, date of birth, and uncovered passwords.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_2.png" height="300" width="1500">

## Lists and Dictionaries
# A list as extracted from database as Python objects.
These are a list and dictionaries that show the users when they are extracted from the database using the debugger.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_11.png" height="400" width="1500">

### Two distinct examples of dictionaries, show Keys/Values using debugger.
The read method creates a dictionary that includes the object's information (ID, user ID, note, image filename, base64-encoded image data). Using a debugger, we can confirm that the dictionary captures these values accurately for different instances of the class, ensuring the proper representation of object data.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_4.png" height="400" width="1500">

## Apis and Json
### Python API code definition for request and response using GET, POST, UPDATE methods. Discuss algorithmic condition used to direct request to appropriate Python method based on request method.
This code manages a Python API's "POST" request. It begins by determining whether the request has the necessary information, such as a note and user ID. If all goes according to plan, this data is added to a new record in the database. It returns the newly created entry if successful. It returns an error message in the event that there is a problem, such as missing data or a duplicate user ID. It works similarly to a form that you fill out, and when you submit it, the data you entered is saved. It notifies you if there is a problem with the information you entered so you can correct it.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_5.png" height="400" width="1500">

### Algorithmic conditions used to validate data on a POST condition.
This little piece of code first determines whether the user ID (uid) is fewer than two characters or absent. If so, an error message stating that the user ID is invalid is returned. Then, it reads other information from the request body, such as the parent post ID and the date of question (doq). Subsequently, it creates a new Post object using the supplied data. In addition, it carries out extra error checking, such changing the date format. This procedure returns an error message indicating the problem if there is a problem. All things considered, this method makes sure that the information sent in the POST request is accurate and correctly formatted before constructing a new post object.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_6.png" height="300" width="1800">

### URL request and Body requirements for GET, POST, and UPDATE methods.
Enabling requests to be routed to the relevant Python methods is based on mapping HTTP to class methods that basically have similar names. The framework makes sure that every request is handled effectively and directed to the appropriate method based on the intended action specified by the HTTP by checking the HTTP method (GET, POST, PUT) and automatically using the corresponding method defined within the resource class (for example, get, post, put).
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_7.png" height="500" width="1500">

### In Postman, show the JSON response data for 200 success conditions on GET, POST, and UPDATE methods.
The URL endpoints for GET, POST, and UPDATE queries are displayed in these photos, along with the necessary body content and arguments for each request. It explains to users how to properly format their queries in order to communicate with the API. These pictures show the JSON response data that the GET, POST, and UPDATE methods of the API return when a request is successful (status code 200). It gives users a preview of the structure and information they should expect from a successfully executed request.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_8.png" height="500" width="1500">

### In Postman, show the JSON response for error for 404 when providing an unknown user ID to a UPDATE request.
This picture displays the JSON response that the API returns when a POST request fails because the body is missing (status code 400). It notifies users of the precise error that happened and might offer advice on how to fix it, like adding the necessary body content. This picture shows the JSON response that the API returns with a 404 error status code when the resource that was requested (the user ID) cannot be located. Users are prompted to confirm that the ID they are trying to update is accurate and are informed that the user ID they have provided does not exist in the system.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_9.png" height="500" width="1250">

### Response of JSON objects from fetch of GET, POST, and UPDATE methods in frontend.
The project in this image is our team's data structures based project, and although it does not require a database for its backend, it satisfies the requirement by offering a flask endpoint of /api/prizepicks/predicted-stats that replies to POST requests from the frontend. Using a machine learning model, the endpoint retrieves predicted stats for a particular matchup number and compares then with the actual stats pulled from an externam database. The frontend receives the conparison results as JSON objects which allows the user to see the results of their selection.
<img src="https://AidanDelgado2.github.io/student2/images/collections_ss_10.png" height="500" width="1500">