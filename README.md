CogniCity
===========
**Open Source GeoSocial Intelligence Framework**

####cognicity-reports-detik: Module for [cognicity-reports](https://github.com/smart-facility/cognicity-reports) module to collect reports from Detik API.

[![Build Status](https://travis-ci.org/smart-facility/cognicity-reports-detik.svg)](https://travis-ci.org/smart-facility/cognicity-reports-detik)

DOI for current stable release [v2.0.0](https://github.com/smart-facility/cognicity-reports-detik/releases/tag/v2.0.0):
[![DOI](https://zenodo.org/badge/19201/smart-facility/cognicity-reports-detik.svg)](https://zenodo.org/badge/latestdoi/19201/smart-facility/cognicity-reports-detik)

### About
Cognicity-reports-detik is the NodeJS reports module for collecting relevant articles from the Detik API. For detailed framework documentation see [http://cognicity.info](http://cognicity.info).
This module is not designed to be run standalone but is designed to be run as a submodule of [cognicity-reports](https://github.com/smart-facility/cognicity-reports), which can run just with this submodule alone.

### API Documentation
[http://cognicity.info/cognicity/api-docs/cognicity-reports-detik/index.html](http://cognicity.info/cognicity/api-docs/cognicity-reports-detik/index.html)

### Dependencies
* [NodeJS](http://nodejs.org) version 4.2.1 or compatible

#### Dev Modules
* [jshint](https://github.com/jshint/node-jshint) version 2.8.0 or compatible
* [unit.js](http://unitjs.com/) version 1.0.2 or compatible
* [mocha](http://mochajs.org/) version 2.0.1 or compatible
* [jsdoc](https://github.com/jsdoc3/jsdoc) version 3.2.0 or compatible
* [istanbul](https://github.com/gotwarlost/istanbul) version 0.3.5 or compatible

If you're going to commit changes to the JavaScript, be sure to run 'npm test' first - and fix any issues that it complains about, otherwise the build will fail when you push the commit.

### Installation
Please install this as a submodule of [cognicity-reports](https://github.com/smart-facility/cognicity-reports). Please refer to the [documentation of that project](https://github.com/smart-facility/cognicity-reports/blob/master/README.md) for further information.

Install the node dependencies for this submodule as listed in package.json using npm: `npm install`

#### Platform-specific notes ####
To build on OS X we recommend using [homebrew](http://brew.sh) to install node, npm, and required node modules as follows:
```shell
brew install node
npm install
```

To build on Windows we recommend installing all dependencies and running `npm install`.

### Configuration
App configuration parameters are stored in a configuration file which is parsed by DetikDataSource.js. See sample-detik-config.js for an example configuration.

#### Detik parameters
* serviceURL - URL to the Detik service API, including topic number. E.g. https://example.com/latest?topic=2
* pollInterval - How long to wait between checking the URL for new articles, in milliseconds. E.g. 1000 * 60 * 5 = 5min
* historicalLoadPeriod - How old an article can be and still be processed, in milliseconds. E.g. 1000 * 60 * 60 = 1hr
* pg.table_detik - Database table used to store Detik reports
* pg.table_detik_users - Database tables used to store Detik report counts per user

### Development

#### Testing

To run the full set of tests, run:

```shell
npm test
```

This will run the following tests:

##### JSHint

JSHint will run on all JavaScript files in the root folder and test folders.

Running the script:

```shell
npm run jshint
```

This will print an error to the screen if any problems are found.

##### Mocha

Mocha will run all unit tests in the test folder and can be run with the following script:

```shell
npm run mocha
```

The test output will tell you how many tests passed and failed.

#### Git Hooks

There is a git pre-commit hook which will run the 'npm test' command before your commit and will fail the commit if testing fails.

To use this hook, copy the file from 'git-hooks/pre-commit' to '.git/hooks/pre-commit' in your project folder.

```shell
cp git-hooks/pre-commit .git/hooks/
```

#### Documentation

To build the JSDoc documentation run the following npm script:

```shell
npm run build-docs
```

This will generate the API documentation in HTML format in the `docs` folder, where you can open it with a web browser.

#### Test Coverage

To build test code coverage documentation, run the following npm script:

```shell
npm run coverage
```

This will run istanbul code coverage over the full mocha test harness and produce HTML documentation in the directory `coverage` where you can open it with a web browser.

#### Release

The release procedure is as follows:
* Update the CHANGELOG.md file with the newly released version, date, and a high-level overview of changes. Commit the change.
* Create a tag in git from the current head of master. The tag version should be the same as the version specified in the package.json file - this is the release version.
* Update the version in the package.json file and commit the change.
* Further development is now on the updated version number until the release process begins again.

### License
This software is released under the GPLv3 License. See License.txt for details.
