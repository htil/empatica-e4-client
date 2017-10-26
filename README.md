# empatica_e4-client

empatica_e4-client is a node.js module, which can communicate with Empatica BLE Server to fetch the sensor stream data from the Empatica E4 device. 

Intruction to setup the Emaptica BLE Server is provided in link (http://developer.empatica.com/windows-ble-server.html)

# Dependencies 
Binstring (https://www.npmjs.com/package/binstring)
net (https://www.npmjs.com/package/net) 

# Installation
```sh
$ cd <project_path>
$ npm install empatica_e4-client
```
# Demo
```javascript
var EmpaticaE4 = require('empatica_e4-client');
var dev1 = new EmpaticaE4();

dev1.connect(28000,'127.0.0.1','XX1234', function(data){  
	var str = EmpaticaE4.getString(data);
	console.log(str);
});
setTimeout(function() {
	dev1.subscribe(EmpaticaE4.E4_BVP);
	dev1.subscribe(EmpaticaE4.E4_ACC);
}, 1000);
```