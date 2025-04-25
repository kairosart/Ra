
To create a **temporary Docker environment** on Kali Linux (or any Debian-based distro), you can spin up an isolated container with everything you need — without polluting your host system. Here's how to do it:

---

## Step-by-Step: Temporary Docker Environment on Kali Linux

### 1. **Make sure Docker is installed**

If it’s not:

### **2. Enable X11 forwarding to the container**

This lets GUI apps inside Docker use your host’s display.

#### Step-by-step:

#Attacking_Machine 
1. On your **host**, allow X11 connections:
```
xhost +
```

2. Start the Docker container with X11 support:
```
docker run -it \   --env DISPLAY=$DISPLAY \   --volume /tmp/.X11-unix:/tmp/.X11-unix \   --name spark-gui ubuntu bash
```

#Docker 
3. Install  *openjdk-8-jre | oracle-java8-jre*.

```
apt update && apt install openjdk-8-jre
```

#Docker 
4. Install *spark_2_8_3.deb*. 
```
dpkg -i spark_2_8_3.deb 
```

5. Run spark.
```
spark
```

![[Docker-20250425122426535.webp]]

