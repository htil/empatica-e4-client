# empatica-e4-client

empatica-e4-client is a node.js module, which can communicate with Empatica BLE Server to fetch the sensor stream data from the EmpaticaE4 device. 

Intruction to setup the Emaptica BLE Server is provided in link (http://developer.empatica.com/windows-ble-server.html)

# Dependencies 
Binstring (https://www.npmjs.com/package/binstring)
net (https://www.npmjs.com/package/net) 

# Installation
```sh
$ cd <project_path>
$ npm install empatica_e4-client
```
# Subscribe Options
```code
	EmpaticaE4.E4_ACC					//3-axis accleration
	EmpaticaE4.E4_BVP   				//Blood Volume Pulse
	EmpaticaE4.E4_GSR   				//Galvanic Skin Response
	EmpaticaE4.E4_TEMP  				//Skin Temperature
	EmpaticaE4.E4_IBI					//Interbeat Interval
	EmpaticaE4.E4_BATT					//Device Battery
	EmpaticaE4.E4_TAG					//Device Tag
```

# Demo
```javascript
var EmpaticaE4 = require('empatica_e4-client');
var dev1 = new EmpaticaE4();

var portNumber  = 28000;
var ipAddress   = '127.0.0.1';
var deviceID    = 'XX1234';        //Empatica E4 device ID 
dev1.connect(portNumber ,ipAddress, deviceID, function(data){  
	var sensorData = EmpaticaE4.getString(data);
	console.log(sensorData);
});
setTimeout(function() {
	dev1.subscribe(EmpaticaE4.E4_BVP);
	dev1.subscribe(EmpaticaE4.E4_ACC);
}, 1000);
```
