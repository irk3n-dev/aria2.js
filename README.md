aria2.js
========

JavaScript library for [aria2, "The next generation download utility."](http://aria2.sourceforge.net/)

[![NPM version](https://badge.fury.io/js/aria2.png)](https://npmjs.org/package/aria2)
[![Build Status](https://travis-ci.org/sonnyp/aria2.js.png?branch=master)](https://travis-ci.org/sonnyp/aria2.js)

[![Dependency Status](https://david-dm.org/sonnyp/aria2.js.png)](https://david-dm.org/sonnyp/aria2.js)
[![devDependency Status](https://david-dm.org/sonnyp/aria2.js/dev-status.png)](https://david-dm.org/sonnyp/aria2.js#info=devDependencies)

## Use

### Install
```
npm install aria2
```

### Browsers
```xml
<script src="aria2.js/lib/index.js"></script>
```

### Node.js
```
var aria2 = require('aria2');
```

### Example

```javascript
var aria2 = new Aria2();

aria2.open('ws://127.0.0.1:6800/jsonrpc')

aria2.onopen = function() {
  console.log('OPEN');

  //aria2 method
  aria2.getVersion(function(err, res) {
    console.log(err || res);
  });
};
aria2.onclose = function() {
  console.log('close');
};
aria2.onsend = function(m) {
  console.log('message out:')
  console.log(m);
};
aria2.onmessage = function(m) {
  console.log('message in:');
  console.log(m);
};

//aria2 notification
aria2.onDownloadStart = function(e) {
  console.log(e);
};
```

## Methods
See [aria2 methods](http://aria2.sourceforge.net/manual/en/html/aria2c.html#methods)

For every method you can use
```javascript
aria2.send(method, [params], function(err, res) {
  console.log(err || res);
});
```

or directly
```javascript
aria2.method([params], function(err, res) {
  console.log(err || res);
});
```

## Notifications
See [aria2 notifications](http://aria2.sourceforge.net/manual/en/html/aria2c.html#json-rpc-over-websocket)

For every notifications you can attach a function to call.
```javascript
aria2.onDownloadStart = function(event) {
  console.log(event);
};
```
