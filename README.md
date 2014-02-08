===============================================
Django/Angular Project Seed
===============================================

A project template for AngularJS, Django 1.6 and Heroku.

Initial setup
-------------

Create your virtual environment.
-In your Django backend folder, run "pip install -r requirements.txt."
--windows os will have to install bower manually from the backend folder with full path

```

```

-In your AngularJS frontend folder, run "npm install."

Setting up your database
-------------------------

- python manage.py schemamigration public —-init
- python manage.py syncdb
--Select "no." Do not create a superuser at this time.
- python manage.py migrate
- python manage.py createsuperuser
- python manage.py schemamigration public —-auto // Nothing seems to have changed.

Deploying to Heroku
-------------------
- Create a new heroku account at heroku.com
- Open up your terminal
- Run the following commands

```
cd /path/that/will/hold/repository
git clone git@github.com:test.git # using the same name as above for an example
cd test
heroku create # this will create a new heroku app and attach it as a remote repository
```

- Copy the heroku app domain to the ALLOWED_HOSTS array in project/settings/test.py

```
git push heroku master
heroku open # run this once the previous command finishes, it may take a minute
```



# The seed for Django and AngularJS

This project is an application skeleton.  It uses the Bower package manager to handle
front-end dependencies, NodeJS to handle the Web server and Karma (a NodeJS dependency) to run unit tests.

### Running the app during development

* Make sure that NodeJS is installed
* From the CLI, in the project directory, run `npm install`

You can run the NodeJS server in two ways:

* Run `server/web-server.js` from the CLI
* Set up a NodeJS configuration in IDE

Then navigate your browser to `http://localhost:<port>/public/index.html` to see the app running in
your browser.

### Running unit tests

Requires [node.js](http://nodejs.org/), Karma (`sudo npm install -g karma`) and a local
or remote browser.

* start `developer/test/scripts/test.sh` (on windows: `developer\test\scripts\test.bat`)
  * a browser will start and connect to the Karma server (Chrome is default browser, others can be captured by loading the same url as the one in Chrome or by changing the `config/karma.conf.js` file)
* to run or re-run tests just change any of your source or test javascript files

### End to end testing

Angular ships with a baked-in end-to-end test runner that understands angular, your app and allows
you to write your tests with jasmine-like BDD syntax.

Requires a webserver, node.js + `./server/web-server.js` or your backend server that hosts the angular static files.

Check out the
[end-to-end runner's documentation](http://docs.angularjs.org/guide/dev_guide.e2e-testing) for more
info.

* create your end-to-end tests in `developer/test/e2e/scenarios.js`
* serve your project directory with your http/backend server or node.js + `server/web-server.js`
* to run do one of:
  * open `http://localhost:port/test/e2e/runner.html` in your browser
  * run the tests from console with [Karma](http://karma-runner.github.io) via
    `developer/test/scripts/e2e-test.sh` or `developer/test/scripts/e2e-test.bat`

## Directory Layout

    .bowerrc                    --> Configures bower to install components under public/lib
    .gitignore                  --> Artifacts we do not want in our git repositories, switched based on where we are pushing changes
    bower.json                  --> Declares front-end dependencies, like angular and bootstrap
    LICENSE                     --> Officially declaring this code under MIT licenses
    package.json                --> Declares dev and prod dependencies, for prod it will install bower
    Procfile                    --> File required by Heroku to launch your application
    README.md                   --> This file

    developer/
        config/
            karma.conf.js        --> config file for running unit tests with Karma
            karma-e2e.conf.js    --> config file for running e2e tests with Karma
        test/
            e2e/              -->
                runner.html     --> end-to-end test runner (open in your browser to run)
                scenarios.js    --> end-to-end specs
            lib/
                angular-mocks.js
                angular-scenario.js
                version.txt
            scripts/            --> handy shell/js/ruby scripts
                e2e-test.sh       --> runs end-to-end tests with Karma (*nix)
                e2e-test.bat      --> runs end-to-end tests with Karma (windows)
                test.bat          --> autotests unit tests with Karma (windows)
                test.sh           --> autotests unit tests with Karma (*nix)
            unit/                     --> unit level specs/tests
                controllersSpec.js      --> specs for controllers
                directivessSpec.js      --> specs for directives
                filtersSpec.js          --> specs for filters
                servicesSpec.js         --> specs for services

    public/                     --> all of the files to be used in production
      css/                      --> css files
        app.css                 --> default stylesheet
      img/                      --> image files
        portfolio-one.gif       --> Cheetos image for the portfolio page
      index.html                --> app layout file (the main html template file of the app)
      js/                       --> javascript files
        app.js                  --> angular application config, run and routes
        constants.js            --> angular constants
        controllers.js          --> angular controller portion of MVC
        directives.js           --> angular directives, contains a 'toggling' example
      json/
        portfolio-data.json     --> contains dummy portfolio data that can be updated
      partials/                 --> angular view partials (partial html templates)
        about.tpl.html          --> contains the about page content, demonstrates angularjs filters
        contact.tpl.html        --> contains the contact page content
        home.tpl.html           --> contains the home page content
        portfolio.tpl.html      --> contains the portfolio page content, demonstrates angularjs data binding, looping and JSON consumption

    server/
        web-server.js     --> simple development web server based on node.js

