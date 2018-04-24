# Configuration

## Environmental variables & JSON config {#environmental-variables-and-json-config}

In your environmental variables you can optionally specify a path to your configuration JSON file. By default, system will be looking for `config.default.json` in the root of your project.

```text
CONFIG_PATH             // Path to your configuration file
```

The JSON config may look something  like this:

{% code-tabs %}
{% code-tabs-item title="config.json" %}
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
{% endcode-tabs-item %}
{% endcode-tabs %}

Comment for each value is:

```text
server.name            - Name of the server
server.url             - Client facing URL of the server, if not set, system will try to read X-Forwarded-Proto header (see Nginx, etc). Should even that be missing, http://localhost:8080 will be used. (optional)
server.max_upload      - Max file size to be uploaded onto the server as a Data file. (optional, default is 50Mb)

jwt_secret             - You have to set the secret to run Boost in production mode

database.host          - Database host (optional, default localhost)
database.port          - Database port (optional, default 5432)
database.name          - Database name
database.user          - Login username
database.password      - Login password
database.logging       - Enable logging for your SQL queries (default false)
```

