# Middleware-setup

[![Build Status](https://travis-ci.org/jadok/middleware-setup.svg?branch=master)](https://travis-ci.org/jadok/middleware-setup)
[![Coverage Status](https://coveralls.io/repos/github/jadok/middleware-setup/badge.svg?branch=master)](https://coveralls.io/github/jadok/middleware-setup?branch=master)

This library implement the middleware setup to setup your application.
This provide you the ability to setup your application through severals **async** tasks.

## Installation

This is a [Node.js](https://nodejs.org/en/) module available through the
[npm registry](https://www.npmjs.com/). Installation is done using the
[`npm install` command](https://docs.npmjs.com/getting-started/installing-npm-packages-locally):

```sh
$ npm install middleware-setup
```

## How it works

### Implement Task

[Task](./src/task.js) is one of the key.
Implements

```javascript
var { Task } = require('middleware-setup');

class MyTask extends Task {
  async execute() {
    // Do something cool here.
    return (42); // the right answer :)
  }
}

module.exports = MyTask
```

### Setup the runner

```javascript
var { runner } = require('middleware-setup');
var someTask = require('./customTask');

runner([
  // list of task
  new someTask(),
  new someTask()
])
  .then(() => console.log('Tasks done'))
  .catch(err => console.error('A task failed', err))

```

Some examples [here](./example/sample.js)

## Credit

- Highly inspired by [Tournamenter](https://github.com/TendaDigital/Tournamenter/blob/master/app.js)
