
#Fragen
https://answers.sap.com/questions/485740/xs-advanced-schema-privilge-trigger-in-sps03-remov.html

# TODO zu SPS03
- sap ui 5 service broker: https://github.com/SAP/com.sap.openSAP.hana5.example/commit/6e07564c805858a6b4765d5cb786c83aaad198fc
- audit log auf v2
- hdbrole TRIGGER
- secure storage
- neue node version zum laufen bekommen
- package.json dependencies updaten

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

## Notifications:
	- Slack (https://github.com/slackapi/node-slack-sdk + https://api.slack.com/incoming-webhooks)
	- REST/ODATA (https://nodejs.org/api/https.html + https://nodejs.org/api/http.html) Normales REST mit möglichst vielen verschiedenen Optionen
	- Email (https://nodemailer.com/about/)
	- Stride (ehemals Hipchat) (https://developer.atlassian.com/cloud/stride/learning/messages/) vll. am Anfang nur mit Room Tokens
	- Android + iOS Push mit Firebase (https://firebase.google.com/docs/admin/setup + https://firebase.google.com/docs/cloud-messaging/admin/send-messages)
	- SMS (https://www.twilio.com/docs/sms/quickstart/node  + https://support.twilio.com/hc/en-us/articles/223181348-Getting-started-with-Alphanumeric-Sender-ID?_ga=2.136626035.219436478.1523002177-227377952.1523002177)
	- Cisco Jabber (https://developer.cisco.com/site/jabber-bots/ + https://botkit.ai/docs/readme-pipeline.html#send)
	- Hangout chat (https://developers.google.com/hangouts/chat/ + https://developers.google.com/hangouts/chat/quickstart/incoming-bot-python)
	
	- Cisco Jabber (https://developer.cisco.com/site/collaboration/ , https://developer.cisco.com/site/jabber-websdk/overview/ + https://developer.cisco.com/site/jabber-websdk/learn/im-and-presence-how-to/use-jabber-im-core-apis/)
	- SOAP Call (vmtl nicht notwendig
	- RFC Call (https://github.com/SAP/node-rfc) fuktioniert vml nicht
	- Einfach nur loggen (SAP Audit Log)
	- Skype (https://dev.skype.com/bots + https://docs.microsoft.com/en-us/azure/bot-service/nodejs/bot-builder-nodejs-message-create)

