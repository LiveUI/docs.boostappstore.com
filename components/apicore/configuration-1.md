# Configuration

```text
CONFIG_PATH         // Path to your configuration file
```

The JSON config may look like this

```swift
{
	"server": {
		"name": "Booster!",
		"url": "http://localhost:8080",
		"max_upload": 50
	},
	"jwt_secret": "secret",
	"database": {
		"host": "localhost",
		"port": 5432,
		"user": "boost",
		"password": "aaaaaa",
		"database": "boost",
		"logging": true
	},
	"mail": {
		"mailgun": {
			"domain": "sandbox-domain.mailgun.org",
			"key": "secret-key"
		}
	}
}
```

**server.name** - Name of the server  
**server.url** - Client facing URL of the server, if not set, system will try to read `X-Forwarded-Proto` header \(see Nginx, etc\). Should even that be missing, `http://localhost:8080` will be used. _\(optional\)_  
**server.max\_upload** - Max file size to be uploaded onto the server as a Data file. _\(optional, default is 50Mb\)_

**jwt\_secret** - You have to set the secret to run Boost in production mode

**database.host** - Database host _\(optional, default `localhost`\)_  
**database.port** - Database port _\(optional, default `5432`\)_  
**database.name** - Database name  
**database.user** - Login username  
**database.password** - Login password  
**database.logging** - Enable logging for your SQL queries _\(default false\)_

