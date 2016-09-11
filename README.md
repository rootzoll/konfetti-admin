# Konfetti - Admin GUI

I web GUI for administration of Konfetti API. Based on RDash rdash-angular.

Part of the Konfetti project: https://github.com/rootzoll/konfetti-app

rdash-angular is an AngularJS implementation of the RDash admin dashboard. The dashboard uses a small number of modules to get you started, along with some handy directives and controllers to speed up development using the dashboard.

## Usage

### Requirements
* [NodeJS](http://nodejs.org/) (with [NPM](https://www.npmjs.org/))
* [Bower](http://bower.io) `npm install bower -g`
* [Gulp](http://gulpjs.com) `npm install gulp -g`

### Installation
1. Clone the repository: `git clone https://github.com/rootzoll/konfetti-admin`
2. Install the NodeJS dependencies: `npm install`.
3. Install the Bower dependencies: `bower install`.
4. Run the gulp build task: `gulp build`.
5. Run the gulp default task: `gulp`. This will build any changes made automatically, and also run a live reload server on [http://localhost:8888](http://localhost:8888).

Ensure your preferred web server points towards the `dist` directory.

### Development
Continue developing the dashboard further by editing the `src` directory. With the `gulp` command, any file changes made will automatically be compiled into the specific location within the `dist` directory.