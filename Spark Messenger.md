You can notice that in the same flag;'s directory there some files starting with "spark".
There's a `.deb` file and you can see what its content is.

#smbclient 
- Download the spark* files.
```
mget spark*
```

#Attacking_Machine 
- Look at spark_2_8_3.deb content.
```
dpkg-deb -I spark_2_8_3.deb
```

![[Spark Messenger-20250424121329878.webp]]

### Installing spark

As this program pre-Depends: *openjdk-8-jre | oracle-java8-jre*. You can install this packages following the steps oon [[Install OpenJDK 8 on Kali Linux]].

### If you want to use the `.deb`:

1. **Extract the .deb manually** without installing:
```
dpkg-deb -x spark_2_8_3.deb extracted-spark
```


This unpacks the `.deb` into the `extracted-spark` folder.

2. Search for any `spark` launcher script. In the top extracted folder (where you unpacked `spark_2_8_3.deb` or `.tar.gz`), do:

```
find . -type f -name "spark"cd extracted-spark find . -name "*.jar"
```

Look for small executable files — **not .jar files**.

3. Assuming you're in the folder where you extracted, then:
```
cd usr/share/spark

java -cp "lib/*" org.jivesoftware.launcher.Startup
```

![[Spark Messenger-20250428204457416.webp]]



