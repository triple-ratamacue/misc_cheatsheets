# Cups Tutorial
A quick reference explaining how to set up network printing in linux

### Preparations
1. get root access and download the packages 
``` bash
 sudo -s  
 apt-get update && apt-get install cups
```
2. Add myself to printer admin group
``` bash
usermod -aG lpadmin NAME
```

3. create another user for everyone who'll be granted access to the server, but without any fancy features (no home dir, no bash etc)
``` bash
useradd -c COMMENT -M -s /bin/false NAME
usermod -aG lpadmin NAME
passwd NAME
```

### CONFIGURE CUPS
1. stop process
``` bash
service cups stop
```

**the following steps all take place in /etc/cups/cupsd.conf, MAKE BACKUP FIRST** 

2. enable external access
``` bash
Listen var/run/cups/cups.sock
Port 631
# Listen localhost:631
WebInterface Yes
```

3. Restrict access to server:

``` html
<Location />
  Order allow,deny
  Allow from INSERT_IP-RANGE_HERE
  Require user @SYSTEM 
</Location>
```

4. Restrict access to admin pages:
``` html
<Location /admin>
  Order allow,deny
  Allow from INSERT_IP-RANGE_HERE
  Require user @SYSTEM 
</Location>

<Location /classes>
  Order allow,deny
  Allow from INSERT_IP-RANGE_HERE
  Require user @SYSTEM 
</Location>

<Location /help>
  Order allow,deny
  Allow from INSERT_IP-RANGE_HERE
  Require user @SYSTEM 
</Location>

<Location /jobs>
  Order allow,deny
  Allow from INSERT_IP-RANGE_HERE
  Require user @SYSTEM 
</Location>

<Location /printers>
  Order allow,deny
  Allow from INSERT_IP-RANGE_HERE
  # Require user @SYSTEM # comment, for windows access
</Location>

```

5. Restrict access to configuration files...
``` html
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  Order allow,deny
  Allow from INSERT_IP-RANGE_HERE
</Location>
```

6. save file, exit and restart cups
``` bash
/etc/init.d/cups restart # or service cups restart
```


## CONNECT PRINTER

1. open browser, got to
```http://IPADDR:631/admin```
2. add printer, upload .ppd, select option "shared" 
3. done