# Xcode

If you are using a mac and have Xcode installed on your machine, you can clone the repo and do the installation manually. Feel free to skip the installation steps if you have these tools available.

##### 1. Install Homebrew
```bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

##### 2. Install Vapor Toolbox
```bash
brew tap vapor/homebrew-tap
brew update
brew install vapor
```

##### 3. Clone Boost repo
```bash
git clone git@github.com:LiveUI/Boost.git
```

##### 4. Update all dependencies
```bash
vapor xcode
```
or if you'd like to see what is going on ...
```bash
vapor xcode --verbose
```

##### 5. Open `Boost.xcworkspace` and run `Run` sheme on `My Mac`
   You might also want to check schemes arguments and environmental variables to configure connection to your PostgreSQL database and other parameters needed to run Boost.

> To configure your environmental variables edit Run scheme and see pre-set settings
