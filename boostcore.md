# BoostCore

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

