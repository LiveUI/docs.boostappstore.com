# Configuration

## Environmental variables & JSON config

Environmental variables are being passed to the app at the start and are as follows

```text
// PostgreSQL Database
DB_HOST         // Database host (default is localhost)
DB_PORT         // Database port (default is 5432)
DB_USER         // User (default is root)
DB_PASSWORD     // Password (default is nil)
DB_NAME         // Database name

DB_LOGGING      // Enable logging for your SQL queries (values 1/0 or true/false)

// Filesystem
LOCAL_ROOT      // Root folder for local file storage, if not set, system will use `HOME`

// Security
JWT_SECRET      // 
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

database.host - Database host \(optional, default `localhost`\)  
database.port - Database port \(optional, default `5432`\)  
database.name - Database name  
database.user - Login username  
database.password - Login password  
database.logging - Enable logging for your SQL queries \(default false\)

## Xcode

To configure environmental variables in Xcode, edit the `Run` scheme and set these directly onto the target.

![](https://raw.githubusercontent.com/wiki/LiveUI/Boost/Images/xcode/select-scheme.png)

 \* List of schemes

![](https://raw.githubusercontent.com/wiki/LiveUI/Boost/Images/xcode/edit-scheme.png)

 \* Editting environmental variables in a scheme

> To change a port on which your boost app will be running, enable and edit the `Arguments passed on launch` section.

## Boost core

You can configure Boost in your custom Vapor 3.0 `configure.swift` file, either by using custom environmental variables like here:

```swift
public func configure(_ config: inout Config, _ env: inout Environment, _ services: inout Services) throws {
    var boostConfig = BoostConfig()
    boostConfig.database = DbCore.envConfig(defaultDatabase: "boost")
    try Boost.configure(boostConfig: &boostConfig, &config, &env, &services)
}
```

or just hardcoding the values like this:

```swift
public func configure(_ config: inout Config, _ env: inout Environment, _ services: inout Services) throws {
    var boostConfig = BoostConfig()
    boostConfig.database = DbCore.config(hostname: "localhost", user: "root", password: nil, database: "boost")
    try Boost.configure(boostConfig: &boostConfig, &config, &env, &services)
}
```

You can also enable SQL query logging by setting `DB_LOGGING` environmental variable to `1` or `true`

