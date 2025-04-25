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

As this program pre-Depends: *openjdk-8-jre | oracle-java8-jre*, you can create a temporal Docker Environment on you Kali Linux machine if you need it.


### Copy the spark_2_8_3.deb file from host to container

#Attacking_Machine 

```
sudo docker cp /home/kali/Tryhackme/Ra/spark_2_8_3.deb busy_swirles:/home/
```

## Go to Docker

In the [[Docker]]  section are the instructions to install java and spark.

