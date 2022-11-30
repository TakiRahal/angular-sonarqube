# Angular && SonarQube

The Best way to Analyze Angular Project with SonarQube

## Create new Angular Project

    Run ng new angular

## Configure Sonar with Angular

### Include sonar-scanner as devDependencies in the package.json

    Run npm install sonar-scanner --save-dev

### Create configuration file

Create a file called sonar-project.properties in your Angular root directory and add below attributes

    sonar.host.url=http://localhost:9000
    sonar.login=admin
    sonar.password=admin
    sonar.projectKey=test-app
    sonar.projectName=test-app
    sonar.projectVersion=1.0
    sonar.sourceEncoding=UTF-8
    sonar.sources=src
    sonar.exclusions=**/node_modules/**
    sonar.tests=src
    sonar.test.inclusions=**/*.spec.ts
    sonar.typescript.lcov.reportPaths=coverage/{name-project}/lcov.info
    
    
## Add coverage script

    "scripts": {
        ...
        "coverage": "ng test --code-coverage"
    },

## Integrate Karma code coverage with SonarQube
    "scripts": {
        ...
        "sonar": "sonar-scanner"
    }


### Add karma config : karma.conf.js
    
    https://next.angular.io/guide/testing
    
### Add type 'lcov' for karma.config.js

    ...
    coverageReporter: {
        dir: require("path").join(__dirname, "./coverage/star"),
        subdir: ".",
        reporters: [{ type: "html" }, { type: "text-summary" }, { type: 'lcov' }],
    },


### Create code coverage reports

    Run ng test --code-coverage
    
### Start SonarQube with Docker

    Run -d --name sonarqube -p 9000:9000 -p 9092:9092 
    
### Integrate Karma code coverage with SonarQube Server

    Run script sonar
    
## DEMO 
    
[![IMAGE ALT TEXT HERE](https://github.com/TakiRahal/angular-sonarqube/blob/main/src/assets/demo.png)](https://youtu.be/38aJ0JMolgU)
