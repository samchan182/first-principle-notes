# Backend-Dev

Since backend dev job has the highest demand in this industry.

[← Back to README](../README.md)

## The Six role families
![image](../images/02.png)

## What’s Backend?
The fundamental truth of BackEnd is, it is just a continuous running loop application, to handle the local hardware, and networking both layers. 

Listening -> Process -> Respond

* A server (the physical hardware)—can be understanded as a powerful, large computer, running 24/7
* A database (the memory)—a backup of server, where data is stored
* A application (the logic)—it is running on the server

## What’s port?
A port, is the location of server to receive the client request. The entry door / entry port of the server.
sudo lsof -i -P -n | grep LISTEN
The bush command to know your machine port

## What’s sandbox?
A place for doing everything without actual important space. 

The term “sandbox” is aptly derived from the concept of a child's sandbox—a play area where kids can build, destroy, and experiment without causing any real-world damage.

## What’s the localhost?
In web dev, It means you don’t have the server on the internet, and use your local device as server. Start with http://localhost:{your port}
For example, when you access Google.com, your computer sent a request across internet to remote server. When you access localhost, your computer sends request to itself.

One trick is to use ‘nodemon’ tool in Node Package manager, auto-update the files. 

## Why we need framework?
Framework means a collection of pre-written code.
The functionality is so COMMONLY used, so we don’t have to start coding from scratch. 

## Why “manage.py” in Django (python)?
manage.py is the tiny wrapper that points to Command-line tools of Django in my project. 

## What is the “runserver” command in Django(python)?
When you run the python3 manage.py runserver command, Django’s built-in WSGI server will print one log, for each request in browser. 

But the timezone that Django uses, is the server’s own timezone, sometimes it needs to change. 

To be AWARE is the given address is the loop-back address, it means in this same device. If you use your phone to open the address, it won’t work, due to it’s trying to talk to web server itself. 

## How the IP works in Django (python)?
Inside one local network, every device gets  a private (LAN) IP address (198.168.000.XXX), this is only unique within that internet. This IP only works in same Wi-Fi / LAN, will not works in public internet. 

What if the device inside local network wants to talk to wider internet? Then the NAT (network address translation) to let those private internet to share a single public IP. 

## What is Node.js?
node.js is a runtime-environmental program, It’s asynchronous event-driven JavaScript runtime. Only run process / step when being triggered. 

It’s NOT a programming language, it’s a runtime environment. (A runtime environment (RTE) is the software and hardware infrastructure that supports the execution of a computer program)

The naming of “.JS” , is just a naming identification means this architecture is built specifically for Javascript.  Node and Node.js is the same thing, like CoCo Cola and Coke. 

## Why Node is being created?
Most of website’s fronted is written by Javascript (Node.js is built on Google Chrome V8 engine), it was confined ONLY to one single environment— The Browser. 

But before Node.js, developer need to use different language to handle both frontend & backend. 

TO solve the problem, which frontend and backend can efficiently be developed both together, THEN node.js come out. Node allows JavaScript to run outside the browser, NOT just limited in the browser. 

## Choose CommonJS or ES modules?
ES modules is NOT a modules, is a (Node) feature,  which has been hard-coded into engine. It’s a built-in rule, you don’t have to install them. 

Using require() is commonJS syntax style, it will stop run you code, go to hard drive, read it to the memory(RAM). While ES modules, force you put all you import files on top, whole program will read it first to decide next move. 

TO use it, only need the keyword “import” to replace the older environment CommonJS, the “required()”

## What is “npm i “ command stands for?
After you navigate your project, the npm project will go read the blueprint, the “Package.JSON” file, sourcing the materials, and building the foundation.

## Why adding "type: module" in package json file?
After you run the server, Node will go to hard drive, looking for the configuration (rules of physics)of your code, which is the “package.json” file. 

Change json file into “type module” is TO tell your Node.js runtime, execute it with the ES Modules syntax. 

You want to use modern syntax (like import/export..) instead of old CommonJS syntax. Then NODE will treat every JS file in that folder, as an ECMAScript module (ESM). It means you can use import/export instead of using require() method. 

## What is “PACKAGE.JSON” file?
JSON file, JavaScript Object Notation, is an easy way to store or exchange data. 

When running Node project, It relies on 1000+ of third-party written code. If you need to share, it can NOT be transferred that large, then package.json acts as “blueprint”, it’s like a shopping list, “I need this and that…”. It has NO executable code. While the “Modules” is the “Bricks”, it holds all the external modules that our computer needs to execute. 

Those two commands, “node” and “npm”, it’s two different things, node is the engine only to run the JavaScript code, npm is logistics manager, to deliver external modules.

## Why 2 JSON files?
PACKAGE.JSON is for high-level human readable blueprint. 
The “package.json” is machine-level execution, The “package-lock.json” file is automatically generated by the Node.js engine to lock down the exact physical reality of your node_modules folder.

The lock file is not created by “npm init”, it’s like a shopping list of which modules you program needs to use, created by the logistic manager npm.

## What is dependence?
Dependencies, an external package that your program needs to use to function correctly. There will be a Node-Modules folder is being auto-created to store all the external package. If there is no pre-downloaded “node_modules” folder, you can type “npm install”, that node will go to the json file, the dependencies section, to install the package as you appointed. 

## Why there’s node-module folder in my program?
When you download some modules, node will pull data from network, store them in SSD. Rest inside the node_module folder.

It consumes 0 RAM space. 

When you type “import” in your program, node engine will copy from slow SSD, into your program fast RAM sandbox. 

## What is Express?
Express is a Backend framework (Node is runtime !!), to allow developers use JavaScript to create the backend. 

Powerful combination while using Express + Node. 

NOTE: quote or double quote (“”express”” & “express” ) is NO different in express, they all put one string primitive into memory. 

## Why we need Middleware ?
When client side sent request, it could be only RAW text / logging / error / admin….. It needs to pre-handling / security guard before deciding the request is going through which routes. For example, When user (client) sent information by HTML form, Express framework does not know how to read the user input data. 

It’s like the safeguard of a nightclub, a checkpoint of HTTP request / incoming data. You can customize it. 

“Morgan”is a popular third-party middleware module in express framework. 

## What is HTTP request?
It’s a structured message sent by client (web browser / mobile app) to the server. 

## What is the 5 major routes in HTTP?
(Hypertext transfer protocol)  A connection protocol allow the communication between client request, and server & database respond. 
* GET: "I'm here to look at the house." (Get the request from client)
* POST: "I'm here to build a new house at this location." (Sent by client to server, to create new resources)
* PUT: "I'm here to completely replace the house." (Sent by client to server to replace or update some resources)
* PATCH: "I'm here to renovate a room in the house." (Sent by client to server, to partially update some resources)
* DELETE: "I'm here to demolish the house." (sent by client to server, to delete an existing resource)

## What is HTTP response status code?
The 3-digit code, represented by the response of server, according to client request. 
This is the famous ‘404’ refers to NOT FOUND, ‘200’ refers to SUCCESSFULLY FOUND

Cheat sheet
1** . Hold on
2** . Here you go
3** . Go away
4** . You fuck up
5** .  I fuck up

HTTP is a connection bridge between frontend and backend. Frontend sent the electrical data with IP and port, while backed is listening. And message format is JSON format. 

Backend and database is connected by database driver. 

## What is NPM command means?
Node Package Manager. The NPM is accompanying command-line package manager. We can think it as a tool library, created by millions of developers globally. 

There is website npmjs.com contains all the packages written by globally developer. 

## Why developer use PostMan?
When there is not frontend (user interface), developer cannot test the get/post request when building backend.  

You can think PostMan as “A Fake Client”, sent messages to server. 

Postman is an application that simulates a client (a tool acts as a ‘standalone’ client). It allows you, the developer, to act as the "client" and manually craft and send any type of HTTP request to your server to test your routes.

## What is Routes means in web development?
A visitor (client) wants to go one location in city, he needs to drive a car (request) to go to one location (path). In web development, the path is like each page section  (/about, /user, /contact, ….). Once there is request, we need methods to handle (driving a car, know which way to go).

## Why you use EJS(Embedded JavaScript), not as usual HTML?
Webpage is just a simple text document translated by browser. To separate the frontend code (html+CSS, styling, formatting,…) to backend code (logic, functionality, ….). otherwise, your file is so dense, and overcrowded. HTML just a blueprint of the page, deciding the location of pictures etc…, it’s all static data. 

## How do we efficiently merge dynamic server-side data into static frontend HTML structure without creating a mess?

* EJS: A server-side templating language. You write templates with placeholders and logic, then render them with data using res.render().
* HTML: Static files. No server-side variables or logic.

The term “Embedded” simply means it’s JavaScript being written inside HTML. We can understand EJS is a HTML code mixed with a little of JavaScript.

HTML (structure), CSS (style), and JavaScript (behavior)

## Give me some examples of EJS?
* <% ... %> control flow (no output)
* <%= ... %> print escaped value
* <%- ... %> print unescaped HTML
* <%# ... %> comment (not output)

## What is API (application programming interface)?
A bridge between 2 different platforms to communicate. A agreement on how 2 programs talks to each other by HTTP. 
e.g. An application of knowing current time, use API of time-module for data {13:25:09}

API just a standardized middleman, any functionalities / chunks of code, as long as it’s on position of middleman, it can be regarded as API. 
E.g. you build a repository of chatbot with 1000+ of code and files, people use it for input and output, the repository is API. 

## Why there’re so many types of API?
It’s the architecture style, if API is the language (English), then architecture is the grammar.
Different API architecture is good at different field. Like REST API is prefer for Web Dev. 

## How API URL is constructed?
* API base URL——Usually the domain of api or version.
* Endpoint——Specific name of resources.
* Path parameter——specific series number of resources you want. 
* Query parameter———specific filter to choose particular resources.
* API Key———A secret token to allow you access.

The content sent back by API is JSON format, a little bit different from JS Object format. 

## Why turn your backend/server into RESTful API?
API means you wrap the server/program into input/output interface, to make it more easier access by others. 

NOT only send HTTP between local frontend and backend. 

## What’s the type of API authentication?
1. Without authentication
2. Basic authentication (base64 Encoding)
3. API Key authorization (authorization is more focus on client side, give yourself an access key, while authentication is close to identify user)
4. Token Base authentication. (Sign in google account to use database)

## What problems that AXIOS tool can solved?
To avoid heavy coding by using native Node ‘http’ module. 
We can simmplely use this module to retrieve data from internet. 

## What makes an API RESTful?
1. HTTP methods
2. JSON output
3. Client-Server separation
4. Stateless, each request is responsible to each response. 
5. Resource-based. Accessed by URL.

The internet (World Wide Web) is one of the successful RESTful architectures of API. 

## What is “client” in Google Authentication Platform?
The name “client” is basically your application, try to access google authentication service. 

“Client ID” is the identifier of your application. It tells google which app is asking login. 

“Client select” a private keyword only known your server and google.  

## What’s is Authorized JavaScript Origins?
Your domain which allow google to load / initiate Google OAuth requests. It prevents other website to trigger login by using your Client ID. 

## What is Authorized Redirect URIs? 
After a user logs in on Google's page, Google sends them back to your app at this URL. In your code (config/passport.js:8): callbackURL: 'http://localhost:3000/auth/google/callback' 
This URI must exactly match what you register in Google Console — it's a security check so Google only sends auth results to your actual server, not to an attacker's server.

## What is Database?
It is a place we can store data, and use later.

TWO main families: SQL and nonSQL (SQL is a language, Structured Query Language)

SQL is relational database, while nonSQL is non-relational database. e.g. You have your name and email store is table01 as database, but your blog history will be stored in table02 as database, 2 tables has relation. 

The CRUD functionality: (4 main functionalities of database)
1. Create
2. Read
3. Update
4. Destroy

## Why database is being created?
The fundamental truth is CPU can not handle that amount of data, and you need a hard drive SSD.

Different databases is simply specialized tools, in order to solve different specific problem. 

## What is PostgreSQL
Most used in industry. Open-source, large community, it’s a database server program. You can think PostgreSQL is a database server. You can use Excel as database if handling small program, while larger project need professional database structure, it’s hard to use simple Excel to fix it. 

PostgreSQL is the powerful database platform that stores the data, and the pg package is the necessary tool that allows your JavaScript code to talk to it.

When you import (from “pg”) from NPM, you can think as to use PostgreSQL’s server itself. Normally you give path to your program to find it, it does NOT have to drop the whole program into your working directory. 

## Why using pgAdmin?
PostgreSQL is a server running quietly on background. No buttons, No cursors, …No human interface. 

pgAdmin is a graphical tool that makes it easier for developers to manage and edit data in a PostgreSQL database. Use pgAdmin for manual, direct interaction. 

The PostgreSQL server is separated from the PGAdmin APP. You need to manually make connection unless you have installed package. Each time you edit your PostgreSQL database, it’e like you’re writing your data in local SSD. 

## What’s “servers list” on pgAdmin?
After you use master key to unlock values in PostgreSQL database, you make it connects to pgAdmin.

pgAdmin is like connection profile manager, it’s NOT database itself, it only let you read & edit & manage. 

## What’s  “postgres” database in pgAdmin?
“Postgres” database is configuration database, like control room. It’s the default database. 

## What is “schema” in database?
In pgAdmin, “schema” is like Department in a large company (accountant team, dev team, ….). You wouldn’t look through all your table’s data in your own 

You will put almost all of your tables in “public” schema. You can either use “table” column to directly create table, or use “Query Tool” to write SQL code, SQL is a also universal language. 

## What is “Stack Builder”?
it can think as a mini-app store for your PostgreSQL installation. 


How to create a table in SQL?
CREATE TABLE example1(
	id SERIAL PRIAMRY KEY,
	column1 VARCHAR(45),
	column2 VARCHAR(50),
);

Serial is the postgreSQL generator, the primary key makes sure each ID is unique. 
VARCHAR is variable character, establishes hard ceiling of 50 character of space. 

## Will postgreSQL database shut down when closes pgAdmin?
When you shut down the pgAdmin APP, it’s like the remote control of your TV, your TV(database server) still running / the server has been stored your data, the localhost data is stored in your hard drive or SSD. 

As long as your info in JS file is correct, your program can access your database. Click the server “properties” to make sure “the entry” is correct. 


## What is concurrency problem?
e.g. When one client sent the order into server, while waiting for respond, the other client request the order as well, they both received the same inventory number. 

You can use postgreSQL LOCKs, to physically handle memory space for only used in one time. 

Node.js + Express is capable of handling thousands of requests per second. Your load is far below that.

## Some common SQL commands

For tutorial practice https://sqlbolt.com/lesson/introduction 

Q: Return every column and every row, from the table named movies?
```
SELECT * FROM movices;  
```
Q: Return both year and title columns, from table movies?
```
SELECT YEAR, TITLE FROM movies
```
Q: Find the row where id is 6?
```
SELECT * FROM movies
WHERE id = 6;
```
Q: Find movies not in the year from 2000 to 2010?
```
SELECT * FROM movies
WHERE not year BETWEEN 2000 and 2010;
```
Q: Find movies not directed by John?
```
SELECT Title, Director FROM Movies
WHERE Director NOT LIKE "John%";
```
Q: Find the first 5 movie sorted by director name alphabetically, also show me the next 5 movie
```
SELECT Title, Year FROM Movies
ORDER BY DISTINCT Director ASC -- get rid of repeated name, gets unique director

LIMIT 5 OFFSET 5 -- offset, how many you skip
```
Q: There're 2 tables, one is Movies, the other is boxoffice, the id on boxoffice has additional data for movie info. List all the movies by their ratings in descending order
```
SELECT Title, Domestic_sales, International_sales
FROM Movies
    JOIN Boxoffice
    ON Movies.id = Boxoffice.Movie_id
    -- So far two tables has been combined

ORDER BY Boxoffice.Rating DESC;
```
Q: List all buildings and the distinct employee roles in each building (including empty buildings) 
```
SELECT DISTINCT building_name, role 
FROM buildings 
  LEFT JOIN employees
  -- even if no match tableA and talbe B, then show NULL

    ON building_name = building;
```
Q: Find the name and role of all employees who have not been assigned to a building
```
SELECT Role, name, Building FROM Employees
WHERE Building IS NULL
```
Q: List all movies and their combined sales in millions of dollars
```
-- When you need to add number into two columns, you need a temporary column to make selection

SELECT Title, (Domestic_sales+International_sales)/1000000 AS Combined_sales
FROM Movies
    JOIN Boxoffice
    ON Movies.Id = Movie_id
```
Q: Find the total number of employee years worked in each building, you have 4 worker in building 1e, and 5 workers in building 2e
```
SELECT building, SUM(years_employed) as Total_years_employed
FROM employees
GROUP BY building; 

-- the sum operation will add all the number in years_employed, but by adding GROUP BY operation, it add number only according to same building name
```
Q: Find the total number of years employed by all Engineers, there're rest of 2 role, teacher and cleaner
```
SELECT role, SUM(years_employed)
FROM employees
GROUP BY role
HAVING role = "Engineer";

-- HAVING is operating on formed groups, while WHERE is raw row
```
Q: Find the total domestic and international sales that can be attributed to each director
```
SELECT director, SUM(domestic_sales + international_sales) as Cumulative_sales_from_all_movies
FROM movies
    INNER JOIN boxoffice
        ON movies.id = boxoffice.movie_id
GROUP BY director;

-- INNER JOIN means: only keep rows where a movie has a matching box office record
```

## How GFW works
let's say you're using Clash Verge on Windows. 

1. ALL the https request/traffic all sent it to port 127.0.0.1:7897. The port 7897 is set by default to avoid duplicate port usage. 
2. Clash walk through the rule config file, speicifically saying google.com is needed to go to proxy. 
3. Clash will interrupt the this domian by it's own DNS interrupt, after gettig the real IP, open TCP connect from itself to google server. 

## What is MySQL?
Website needs storage system to handle traffic, which is heavily reading data rather than writing it. It prioritizes permanent storage. 

The multi-threaded architecture database is created, extremely efficient at serving simple, high-concurrency read request. 

## What is Redis?
In 2009, an Italian developer found a website for user bowering. But since the visitor is getting larger, the continuing reading and update of database is making it super slow. 

He use C programming, to write a software, to hold the data in RAM, make it can process thousands of updates pre second. He named it Remote Dictionary Server OR Redis. 

## Spring Boot with Redis?
It's one of the most common combination of software architecture. 

Spring Boot acts the intelligence brain to decide which data needs to cache. And Redis acts a fast-respond machine. 

Redis has no idea what you application does.

![image](/images/06.png)

## Redis debug?
Redis is mostly set-and-forget in industry. 

You only go check it when something feel wrong, like slow respond, stale data, memory pressure. 

Your application will talk to redis, don't have to worry about it. 

If you need a test, launching a new feature that heavily need cache, unless you see the old data, then ignore. 

In industry, use 
- Prometheus + Redis Exporter + Grafana (Those tools are for monitoring and altering)
- APM
- Alerts