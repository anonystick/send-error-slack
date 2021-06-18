# send-error-slack
The library helps the system to send errors to slack

The library helps the system to send errors to slack

## Install

```js
$ npm install --save send-error-slack
```
## Usage express without route
```js
const express = require('express')
const sendErrorSlack = require('send-error-slack')

const app = express()

// Route that triggers a error
app.get('/error', function (req, res, next) {
  const err = new Error('Internal Server Error')
  err.status = 500
  next(err)
})

// Send error reporting to Slack
app.use(sendErrorSlack({ webhookUri: 'https://hooks.slack.com/services/TOKEN' }))
app.listen(3000)
```

## Usage express route
```js
/*
    File index.js
*/
var express = require('express'),
    app = express(),
    bodyParser = require('body-parser');

app.use(bodyParser.json()); // support json encoded bodies
app.use(bodyParser.urlencoded({ extended: true })); // support encoded bodies
require('./route')(app); //importing route

/*
    File Route.js
*/
const sendErrorSlack = require('send-error-slack')
const webhookUri = 'https://hooks.slack.com/services/TOKEN';

module.exports = function(app) {
    app.route('/api/checkError').get([TEST_CONTROLLER.checkError])

    // ERRORS
	app.use(sendErrorSlack({webhookUri}))
}
```
## API
```js
const sendErrorSlack = require('send-error-slack')
```

## Author
[Tips Javascript](https://anonystick.com)
