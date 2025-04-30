
Kali removed OpenJDK 8 from default repositories, so **we have to install it manually**.

## Download OpenJDK 8 (official binaries):

#Attacking_Machine 
```
wget https://github.com/adoptium/temurin8-binaries/releases/download/jdk8u392-b08/OpenJDK8U-jre_x64_linux_hotspot_8u392b08.tar.gz
```

## Extract it:

#Attacking_Machine 
```
tar -xvf OpenJDK8U-jre_x64_linux_hotspot_8u392b08.tar.gz
```

This will create a folder like `jdk8u392-b08-jre`.

---

## Move it to `/opt/` (system location):

#Attacking_Machine 
```
sudo mv jdk8u392-b08-jre /opt/java8
```

Now Java 8 is stored under `/opt/java8`.

## Set up environment variables (for your shell):

#Attacking_Machine 
Temporary for now (for current terminal):
```
export JAVA_HOME=/opt/java8 export PATH=$JAVA_HOME/bin:$PATH
```


## Check it:

#Attacking_Machine 
```
java -version
```


✅ It should now say something like:

`openjdk version "1.8.0_392" OpenJDK Runtime Environment ...`

**Next step:** [[Spark Messenger]]
