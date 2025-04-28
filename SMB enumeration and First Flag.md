There's a **SMB** port open: *445/tcp   open  microsoft-ds*


## smbmap

**smbmap** is a post-exploitation and enumeration tool used by penetration testers and security researchers to interact with and enumerate information from SMB (Server Message Block) shares on Windows systems. It's particularly useful for identifying misconfigurations, accessible shares, and even downloading/uploading files if permissions allow.

### Key Features

- Enumerate SMB shares

- Check permissions (READ, WRITE, EXECUTE)

- Download/upload files

- Execute commands remotely (if access permits)

- Identify share and directory access rights quickly

### Run smbmap

#Attacking_Machine 
```
smbmap -u lilyle -p ChangeMe#1234 -d windcorp.thm -H fire.windcorp.thm 
```

![[Enumeration-20250424110800702.webp]]


## smbclient

Run smbclient to see what there is on the Shared Disc.

```
smbclient \\\\10.10.189.54\\Shared -U lilyle%ChangeMe#1234
```

![[Enumeration-20250424113042729.webp]]


## First flag

#smbclient
```
get "Flag 1.txt"
```

#Attacking_Machine 
```
cat 'Flag 1.txt'
```


>[!Success]
THM{466d52dc75a277d6c3f6c6fcbc716d6b62420f48}   


**Next step:** [[Spark Messenger]]
