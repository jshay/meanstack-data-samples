<a href='https://travis-ci.org/garystafford/meanstack-data-samples'><img src='https://travis-ci.org/garystafford/meanstack-data-samples.svg?branch=master'></a>

## Retrieving and Displaying Data with AngularJS and the MEAN Stack
### Overview

Project created for 2-part blog post series: [Retrieving and Displaying Data with AngularJS and the MEAN Stack](http://wp.me/p1RD28-16F). Explore various methods of retrieving and displaying data using AngularJS and the MEAN Stack. Corresponding GitHub project is based on William Lepinski’s [generator-meanstack](https://github.com/wlepinski/generator-meanstack), with Mongoose and Twitter Bootstrap added.

Contains examples of retrieving data using various AngularJS methods:
* Function within AngularJS controller returns array of strings.
* AngularJS Service returns an array of simple object literals to the controller.
* AngularJS Factory creates a resource object to return the contents of JSON file to the controller (Modified 5/2014).
* AngularJS Factory returns a collection of documents from MongoDB Database to the controller.
* AngularJS Factory returns results from Google's RESTful Web Search API to the controller.

### Project Instructions
* Review the [generator-meanstack](https://github.com/wlepinski/generator-meanstack) `README.md`
* Project requires MongoDB, Node, Express, and yo
* Set the `NODE_ENV` environment variable to `test`
* Set the `CHROME_BIN` environment variable for Karma  
(i.e. `C:\Program Files (x86)\Google\Chrome\Application\chrome.exe`

##### Create and Populate MongoDB Test Database
To create the sample database, collection, and documents, you can run the following
JavaScript file, using node:

```
node mongo-setup.js
```
Or, you can manually run the individual command:
```
mongod # starts core database process
mongo # starts interactive MongoDB Shell

use meanstack-test // creates database if it doesn't exist
db.components.insert({ "component": "mongod", "description": "core database process" })
db.components.insert({ "component": "mongos", "description": "controller and query router for sharded clusters" })
db.components.insert({ "component": "mongo",  "description": "interactive MongoDB Shell" })
db.components.insert({ "component": "mongodump",  "description": "utility for creating binary export of database contents" })
db.components.insert({ "component": "mongorestore",  "description": "writes data from a binary database dump to a MongoDB instance" })
db.components.insert({ "component": "mongooplog",  "description": "polls operations from the replication oplog" })
show collections // verifies collection was created
db.components.find() // verifies documents were created
```

##### Install and Configure the Project

```
npm install -g generator-meanstack
git clone https://github.com/garystafford/meanstack-data-samples.git
cd meanstack-data-samples
npm install
grunt
grunt server
```

### Notes About Project
* Original project based on yeoman's [generator-angular](http://yeoman.io/). All generator commands work.
* Link to main AngularJS `test-bootstrap` view: [http://localhost:3000/#](http://localhost:3000/#).
* HTTP GET call to MongoDB data: [http://localhost:3000/api/components](http://localhost:3000/api/components).
* Deferred and Promises used to perform actions asynchronously: [$http](http://docs.angularjs.org/api/ng/service/$http)
* Karma unit tests included for controller and services.
* Karma's default port `8080` to `8090` in `karma.conf.js` and `karma-e2e.conf.js` files. It conflicted with my installation of Apache and every other application that wants to use port `8080` by default.
* The `grunt` command now runs without error. In the original project, `jshint` had a strict violation with `validthis`.
* Added support for Travis-CI. Project now building on [Travis-CI](https://travis-ci.org/garystafford/meanstack-data-samples) for each commit to GitHub (Added 4/2014).

Preview of project on Chrome for Android:

![Chrome on Android ](https://github.com/garystafford/meanstack-data-samples/blob/master/public/images/AndroidMobileView.png?raw=true)
