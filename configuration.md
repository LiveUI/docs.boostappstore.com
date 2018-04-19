# Configuration

## Environmental variables

Environmental variables are being passed to the app at the start and are as follows
```
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
JWT_SECRET      // You have to set the secret to run Boost in production mode


```

## Xcode

To configure environmental variables in Xcode, edit the `Run` scheme and set these directly onto the target.

<p>
   <img src="https://raw.githubusercontent.com/wiki/LiveUI/Boost/Images/xcode/select-scheme.png" alt="" />
   <i><small>* List of schemes</small></i>
</p>

<p>
   <img src="https://raw.githubusercontent.com/wiki/LiveUI/Boost/Images/xcode/edit-scheme.png" alt="" /> 
   <i><small>* Editting environmental variables in a scheme</small></i>
</p>

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

