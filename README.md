# jasmine-bamboo-reporter-nolock
[![view on npm](http://img.shields.io/npm/v/jasmine-bamboo-reporter-nolock.svg?style=flat)](https://www.npmjs.org/package/jasmine-bamboo-reporter-nolock)
[![npm module downloads per month](http://img.shields.io/npm/dm/jasmine-bamboo-reporter-nolock.svg?style=flat)](https://www.npmjs.org/package/jasmine-bamboo-reporter-nolock)

> A reporter for Jasmine which produces a report compatible with Atlassian Bamboo Mocha Test Parser. (forked from https://github.com/voidberg/jasmine-bamboo-reporter) This package does NOT support "'test sharding' or multiple instances of Jasmine running via Protractor" claimed by https://github.com/voidberg/jasmine-bamboo-reporter as the lock mechanism has been removed.

I had no luck to have the forked package running in my environment, it just always created a lock file, but not the report. As my requirement is to run the tests in a single thread, I just removed the locking mechanism and it then worked well for my purpose. Hope this package can help others in the same situation.

## Installation

```sh
npm install jasmine-bamboo-reporter-nolock
```

## Usage

### Jasmine Usage
```javascript
var JSONReporter = require('jasmine-bamboo-reporter-nolock');
jasmine.getEnv().addReporter(new JSONReporter({
	file: 'jasmine-results.json', // by default it writes to jasmine.json
	beautify: true,
	indentationLevel: 4 // used if beautify === true
}));


```

### Protractor/Jasmine Usage
```javascript
// in Protractor conf
var JSONReporter = require('jasmine-bamboo-nolock');
var fs = require('fs');

exports.config = {

framework: 'jasmine2',

...
 
onPrepare: function() {
	jasmine.getEnv().addReporter(new JSONReporter({
		file: 'jasmine-results.json', // by default it writes to jasmine.json
		beautify: true,
		indentationLevel: 4 // used if beautify === true
	}));
}
```

## License

[MIT](https://github.com/nanchen/jasmine-bamboo-reporter-nolock/blob/master/LICENSE)
