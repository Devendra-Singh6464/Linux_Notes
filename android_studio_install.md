## Install Android studio------

### Required libraries for 64-bit machines--- 
### If you are running a 64-bit version of Ubuntu, you need to install some 32-bit libraries with the following command:

```
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386
```


6. go `.bashrc` and add thses line 
```
export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin
```

1. Download tar android file.
2. Extract there.
3. install your required java and jdk file
4. copy android extract file and paste /opt/   folder.
5. cd /opt/android-studio/bin/ ./studio.sh

  
# install---
```
apt install openjdk-21-jdk
```

6. go `.bashrc` and add thses line 
```
export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
export PATH=$PATH:$JAVA_HOME/bin
```


best way 

set android studio desktop icon.
``` cd /usr/share/applications ```
create desktop file-

``` vi android.desktop ```

and paste this-
```

[Desktop Entry]
Type=Application
Name=Android Studio
Exec="/home/users/devendra.singh/Downloads/android-studio/bin/studio.sh" %f
Icon=/home/users/devendra.singh/Downloads/android-studio/bin/studio.png
Categories=Development;IDE;
Terminal=false
StartupNotify=true
StartupWMClass=jetbrains-android-studio
Name[en_GB]=android-studio.desktop

```

Exec / Icon : your android studio downloads folder path 
