# centrofi
_centrofi is an example of how an angular application is deployed in heroku_

## Starting
_You should create an angular project and create an account in heroku_

### Configuration
Create a file called **server.js** to create an Express server and add the following:
```
//Install express server
const express = require('express');
const path = require('path');

const app = express();

// Serve only the static files form the dist directory
app.use(express.static(__dirname + '/dist'));
app.listen(process.env.PORT || 8080);

```
The file **"package.json"** should have the structure following:

* Add in "scripts" -> "heroku-postbuild".
* Modify "rxjs": "^6.0.0" to "rxjs": "6.0.0" in dependencies.
* Add in "dependencies" -> "@angular/cli","@angular/compiler-cli" of "devDependencies" section.
* Add in "devDependencies" -> "typescript"
* Add the "engines" section, the "node" version is consulted with the node -v command and the "npm" version with the npm -v command.

**_All the added changes are described with a *_**
```
{
  "name": "centrofi",
  "version": "0.0.0",
  "scripts": {
    "ng": "ng",
    "start": "node server.js",
    "build": "ng build",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e",
    *"heroku-postbuild": "ng build --aot --prod"
  },
  "private": true,
  "dependencies": {
    "@angular/animations": "^6.0.3",
    *"@angular/cli": "^7.3.3",
    "@angular/common": "^6.0.3",
    "@angular/compiler": "^6.0.3",
    *"@angular/compiler-cli": "^6.1.10",
    "@angular/core": "^6.0.3",
    "@angular/forms": "^6.0.3",
    "@angular/http": "^6.0.3",
    "@angular/platform-browser": "^6.0.3",
    "@angular/platform-browser-dynamic": "^6.0.3",
    "@angular/router": "^6.0.3",
    "core-js": "^2.5.4",
    "express": "^4.16.4",
    "path": "^0.12.7",
    *"rxjs": "6.0.0",**
    *"typescript": "~2.7.2",**
    "zone.js": "^0.8.26"
  },
  "devDependencies": {
    "@angular-devkit/build-angular": "~0.6.6",
    "@angular/cli": "^7.3.3",
    "@angular/compiler-cli": "^6.1.10",
    "@angular/language-service": "^6.0.3",
    "@types/jasmine": "~2.8.6",
    "@types/jasminewd2": "~2.0.3",
    "@types/node": "~8.9.4",
    "codelyzer": "~4.2.1",
    "enhanced-resolve": "^3.3.0",
    "jasmine-core": "~2.99.1",
    "jasmine-spec-reporter": "~4.2.1",
    "karma": "~1.7.1",
    "karma-chrome-launcher": "~2.2.0",
    "karma-coverage-istanbul-reporter": "~2.0.0",
    "karma-jasmine": "~1.1.1",
    "karma-jasmine-html-reporter": "^0.2.2",
    "protractor": "~5.3.0",
    "ts-node": "~5.0.1",
    "tslint": "~5.9.1",
    "typescript": "~2.7.2"
  },
  *"engines": {
    *"node": "8.10.0",
    *"npm": "5.6.0"
  }
}
```
Modify the file **"angular.json"** and delete the project name in the attribute **"outputPath"**.
```
"outputPath": "dist",
```
#### _These settings must be made you to deploy your application in heroku_
Also I share this [tutorial](https://medium.com/@hellotunmbi/how-to-deploy-angular-application-to-heroku-1d56e09c5147_) if you need more information.

