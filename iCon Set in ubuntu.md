## icon---
 
/usr/local/share/applications# vi firefox.backup 


root@prabhat229:/usr/local/share/applications# vim /usr/share/applications/firefox.desktop 


root@prabhat229:~# cd /usr/local/share/applications/
root@prabhat229:/usr/local/share/applications# ls
firefox.desktop  mimeinfo.cache
root@prabhat229:/usr/local/share/applications# vim firefox.desktop 
root@prabhat229:/usr/local/share/applications# vim /usr/share/applications/firefox.desktop 
root@prabhat229:/usr/local/share/applications# 
root@prabhat229:/usr/local/share/applications# ls
firefox.desktop  mimeinfo.cache
root@prabhat229:/usr/local/share/applications# 
root@prabhat229:/usr/local/share/applications# pwd
/usr/local/share/applications
root@prabhat229:/usr/local/share/applications# mv firefox.desktop firefox.backup
root@prabhat229:/usr/local/share/applications# ls
firefox.backup  mimeinfo.cache


check your where your desktop icon location.
```
cd /usr/share/applications
```
create what app icon you want.
for example:
```
vi android.desktop
```
and write this .
Exec: your android studio installation locations and  script `studio.sh`.
Icon: Your android studio icon location.
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Android Studio
Exec="/home/username/Programs/AndroidStudio/bin/studio.sh" %f
Icon=/home/username/Programs/AndroidStudio/bin/studio.png
Categories=Development;IDE;
Terminal=false
StartupNotify=true
StartupWMClass=jetbrains-android-studio
Name[en_GB]=android-studio.desktop
```




[Desktop Entry]
Type=Application
Name=Pycharm
Exec="/home/users/devendra.singh/Downloads/pycharm-2024.2.2/bin/pycharm.sh" %f
Icon=/home/users/devendra.singh/Downloads/pycharm-2024.2.2/bin/pycharm.png
Categories=Development;IDE;
Terminal=false
StartupNotify=true
# iStartupWMClass=jetbrains-pycharm
Name[en_GB]=pycharm
