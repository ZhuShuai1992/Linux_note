#### install TeamSpeak 3.0.0 Server | Linux


#### Update
> sudo apt-get update
 
#### Setup  [Server DownLoad](https://www.teamspeak.com/downloads.html#server "Download NEW URL")
32bit
> wget http://teamspeak.gameserver.gamed.de/ts3/releases/3.0.13.6/teamspeak3-server_linux_x86-3.0.13.6.tar.bz2

64bit
> wget http://teamspeak.gameserver.gamed.de/ts3/releases/3.0.13.6/teamspeak3-server_linux_amd64-3.0.13.6.tar.bz2

> tar -vxjf teamspeak3-server_linux_amd ...

> cd teamspeak3-server_linux_amd ...

> ./ts3server_startscript.sh start
 
#### Auto Start Script
> cd /etc/init.d

> sudo vim ts3

> \#! /bin/bash<br>
 cd /.../teamspeak3-server_linux...<br>
 ./ts3server_startscript.sh start

> sudo chmod +x /etc/init.d/ts3

> sudo update-rc.d ts3 defaults

 
#### Other Commands
> ./ts3server_startscript.sh restart

> ./ts3server_startscript.sh stop

> ./ts3server_startscript.sh status

 
#### Ports
>9987 UDP (Voice)

>10011 TCP (Server Query)

>30033 TCP (File Server)

 
#### Notes
The command `sudo update-rc.d` ts3 defaults may return a warning. This is to be expected.
After a restart the command `./ts3server_startscript` status may show that the server is dead. This is a bug and the server is online.
Making the auto startup script can break your Ubuntu install. Please double check your commands before restarting the server.



## Other
* backup db
`ts3server.sqlitedb` file


crack


* Change hosts file
1. > Linux: /etc/hosts<br>
Windows: C:\Windows\System32\drivers\etc\hosts<br>
127.0.0.1 accounting.teamspeak.com<br>
127.0.0.1 backupaccounting.teamspeak.com<br>
127.0.0.1 ipcheck.teamspeak.com<br>
127.0.0.1 weblist.teamspeak.com #(only if you don't want to be on the weblist)

On Linux: 
> First step: "./AccountingServerEmulator"
> Second step: "./ts3server_startscript.sh start"

On Windows:
> First step: "AccountingServerEmulator"
> Second step: "ts3server.exe"

#### Auto Start Script
> cd /etc/init.d

> sudo vim ts3

> \#! /bin/bash<br>
  cd /home/ubuntu/application/teamspeak3-server_linux_amd64<br>
  ./AccountingServerEmulator-Linux<br>
  cd /home/ubuntu/application/teamspeak3-server_linux_amd64<br>
  ./ts3server_startscript.sh start

> sudo chmod +x /etc/init.d/ts3

> sudo update-rc.d ts3 defaults