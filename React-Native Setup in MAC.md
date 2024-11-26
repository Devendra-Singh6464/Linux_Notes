refrence link :
1. https://medium.com/@swift3.0devlopment/complete-guide-setting-up-react-native-on-macos-for-ios-and-android-development-1232f2980d2b-1232f2980d2b
2. https://reactnative.dev/docs/set-up-your-environment


1. Install node js https://nodejs.org/en/download/package-manager 
```
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
```
and
```
curl -sL [https://deb.nodesource.com/setup_22.x](https://deb.nodesource.com/setup_22.x) | sudo -E bash -  
sudo apt-get install -y nodejs
```
```
nvm install 22
```
```
node -v
```
```
npm -v
```
-- Node version should be 18 and 20.

2. install cocoapods standard user:
```
sudo gem install cocoapods
```
3. Install JDK (Java Development Kit):[[https://www.oracle.com/in/java/technologies/downloads/#java21]]

After the JDK installation, add or update your `JAVA_HOME` environment variable in `~/.zshrc` (or in `~/.bash_profile`).
```
export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-21.jdk/Contents/Home
```
how to run our react-native project in terminal.
create project.
```
 npx react-native@latest init project1
```
1. go project directory
```
cd /myproject
```
2. run this command.
```
npx react-native run-ios
```

check all this entry available on `vi ~/.zshrc` file.
```
vi ~/.zshrc

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm

[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion

export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk-21.jdk/Contents/Home

export ANDROID_HOME=$HOME/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/platform-tools
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
```

