# Configuration

## Environmental variables & JSON config

Boost is configured through an extended configuration file of **ApiCore**. In this section we wil be only describing properties that are not available in **ApiCore** module. Please refer to this [page](components/apicore.md) for further details.

```text

```

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

