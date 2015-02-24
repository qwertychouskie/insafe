![insafe by the World Wide Web Consortium](https://github.com/w3c/insafe/blob/master/public/insafe-logo.png)

Insafe (previously safe url input checker) is a Nodejs library which resolve and check the safety of an url.

#Insafe API

````javascript
var insafe = require('./lib/insafe');

insafe.check({
    url: 'example.com',
}).then(function(res) {
	console.log(res); // return true if safe, else return false
});
```

#API Safe Url Input Checker

for some methods you can use callback or not. Just few methods require a callback especially.

	var urlChecker = require('safe-url-input-checker')

checkUrlSafety

````javascript
var options = {};
options.blacklist = [
	'joker.com',
	'slade.io',
	'twoface.net',
	'...',
	'magneto.vilain'
];
options.protocolScheme = [
	'http',
	'https',
	'ftp'
];
urlChecker.checkUrlSafety('localhost', function(err, res) {
	console.log(res); // false
});
urlChecker.checkUrlSafety('http://batman.com', function(err, res) {
	console.log(res); // true
});
urlChecker.checkUrlSafety('http://joker.com', function(err, res) {
	console.log(res); // false
}, options);
urlChecker.checkUrlSafety('w3.com', function(err, res) {
	console.log(res); // true
}, options);
````

getIPAddresses (optional callback)
	
````javascript
urlChecker.getIPAddresses('localhost', function(err, res) {
	if(err) throw err;
	console.log(res); // ['127.0.0.1']
});
````

isAddressLocal (optional callback)

````javascript
urlChecker.isAddressLocal('127.0.0.1', function(err, res) {
	if(err) throw err;
	console.log(res) // true
});
````

isHostLocal (requested callback)

````javascript
urlChecker.isHostLocal('google.com', function(err, res) {
	if(err) throw err;
	console.log(res) // false
});
````

isHostBlacklisted (optional callback)

````javascript
var blacklist = [
	'joker.com',
	'slade.io',
	'twoface.net',
	'...',
	'magneto.vilain'
];
urlChecker.isHostBlacklisted('joker.com', blacklist, function(err, res) {
	console.log(res); // true
});
````

isProtocolAcceptable (optional callback)

````javascript
var protocolScheme = [
	'http',
	'https',
	'ftp'
];
urlChecker.isProtocolAcceptable('http', protocolScheme, function(err, res) {
	console.log(res); // true
});
````

resolveAndParseUrl (optional callback)

````javascript
urlChecker.resolveAndParseUrl('google.com', function(err, res) {
	console.log(res) // url object
});
````
