
# TODO:
- https://github.com/SAP/com.sap.openSAP.hana5.example durchgehen und Bibliotheken auf neusten Stand bringen


# Notizen
## seucrestore
Keine Infos zu XSA, muss vmtl in XSJS gemacht werden.
Umsetzung:
	1. Xsjs support hinzufügen (https://github.com/SAP/hana-shine-xsa/tree/master/user-js)
	2. Xsjs testseite von browser aus aufrufen
	3. Innerhalb von xsjs securestorage zum laufen kriegen
	4. Xsjs von xsa aus aufrufen
	5. Xsjs von ausenwelt abkoppeln, nur noch von xsa aus erreichbar

https://answers.sap.com/questions/475747/how-can-securestore-be-used-in-xs-advanced.html

var hdbext = require("sap-hdbext");
var hanaConfig = {
	host: "hxehost",
	port: 39013,
	user: "SYSTEM",
	password: "password"
};


hdbext.createConnection(hanaConfig, function(error, client) {
	if (error) {
		console.log("hdbext createConnection:" + error);
	}else{
		console.log("Connection successfull.");
		
		client.exec("SELECT * FROM \"SYSTEM\".\"TABLE\"", function(error, rows) {
			if(error){
				console.log("Error during direct statement execution: " + error);
			}else{
				console.log(rows);
			}
		});
	}
});

## jobsscheduler
https://help.sap.com/viewer/07b57c2f4b944bcd8470d024723a1631/Cloud/en-US/9b861273d16a41ecbc77b583c7cad5aa.html
