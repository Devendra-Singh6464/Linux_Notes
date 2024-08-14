# Change and update java version in ubuntu ---

1. apt install openjdk-17-jdk
2. update-java-alternatives --set java-17-openjdk-amd64
select java version----
3. update-alternatives --config java
4. update-java-alternatives --set java-11-openjdk-amd64
5. vi .bashrc
edit :  
export JAVA_HOME="/usr/lib/jvm/java-17-openjdk-amd64"
export PATH=$PATH:$JAVA_HOME/bin
6. source ~/.bashrc
7. vi /etc/profile
edit:
export JAVA_HOME="/usr/lib/jvm/java-21-openjdk-amd64"
export JDK_HOME=$JAVA_HOME
export STUDIO_JDK=$JAVA_HOME
export PATH=$JAVA_HOME/bin:$PATH
8. java --version




JAVA_HOME = "/usr/lib/jvm/java-11-openjdk-amd64/bin/java"

export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
export JAVA_HOME=/usr/lib/jvm/java-21-openjdk-amd64
