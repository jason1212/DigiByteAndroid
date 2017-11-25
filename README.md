## DigiByte Android Project

This project is stored in two folders.

digibytej - This is the base Java Library for Digibyte.

digibyte-wallet - This is the Android App


## OSX Build Instructions

Install Android Studio
https://developer.android.com/studio/index.html
Install Android SDK 26 (v8 Oreo)

Install Java JDK
http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

Install Maven
```sh
brew install maven
```

Switch to Maven 3.1 to Make Build Work
```sh
brew install homebrew/versions/maven31
brew link --overwrite maven@3.1
sudo ln -s /usr/local/Cellar/maven31/3.1.1 /usr/local/Cellar/maven/
brew switch maven 3.1.1
```

Clone DigiAndroid
```sh
git clone https://github.com/digibyte/digiandroid.git
```

Navigate to DigiBytej Folder
```sh
cd digibytej
```

Make Build
```sh
mvn clean install -DskipTests
```

Navigate to Checkpoints File
```sh
cd tools
```
Start Up Your Local digibyted core wallet For incoming peer connections

Compile Updated Checkpoints File
```sh
mvn exec:java -Dexec.mainClass=com.google.bitcoin.tools.BuildCheckpoints
```
Copy Checkpoints File to Correct Place

Move checkpoints file located here https://github.com/digibyte/digiandroid/tree/master/digibytej/tools

and replace checkpoints file located here: https://github.com/digibyte/digiandroid/tree/master/digibyte-wallet/wallet/assets

Navigate back to digibyte-wallet directory
```sh
cd ../../
cd dgibyte-wallet
```

Build Wallet
```sh
mvn clean install -DskipTests 
```

Build Release Wallet
```sh
mvn clean install -Prelease -DskipTests
```


## Checklist
Android sdk and the correct api version installed

Java JDK

Apache Maven 3.10

Clone the digiandroid repo

CD into digibytej
```sh
mvn clean install -DskipTests
```

Cd checkpoints  dir
```sh
mvn exec:java -Dexec.mainClass=com.google.bitcoin.tools.BuildCheckpoints
```



Development was done with IntelliJ IDEA 12.1.4. Open the digibytej project to open all projects with proper linking.

This file system also contains the maven files. They should work correctly but test will fail. append -Dmaven.test.skip=true to the command line.
