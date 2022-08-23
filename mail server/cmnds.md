# _CyberPanel_
```
sudo su -
```
```
sh <(curl https://cyberpanel.net/install.sh || wget -O - https://cyberpanel.net/install.sh)
```
>__1  -  1  - Y - N -  Enter - s - n - n - Y__
```
sudo apt update
```
```
sudo apt install ufw
```
[Youtube](https://www.youtube.com/watch?v=8G93NVWkXZk, 'Youtube link')

Please choose to use default admin password 1234567, randomly generate one (recommended) or specify the admin password?
## Removing Cyberpanel

Delete usr/local/requiirements.txt
       usr/local/cyberpanel
       
----
### To check the logs journalctl -f | grep postfix
```
journalctl -f | grep postfix
```
> Output:
```
Aug 23 07:38:23 codingsolution postfix/smtp[4873]: connect to alt1.gmail-smtp-in.l.google.com[2607:f8b0:400e:c00::1b]:25: Network is unreachable
Aug 23 07:38:53 codingsolution postfix/smtp[4873]: connect to alt1.gmail-smtp-in.l.google.com[173.194.202.26]:25: Connection timed out
Aug 23 07:39:23 codingsolution postfix/smtp[4873]: connect to alt2.gmail-smtp-in.l.google.com[142.250.141.26]:25: Connection timed out
```
```
ping alt1.gmail-smtp-in.l.google.com
```
```
telnet alt1.gmail-smtp-in.l.google.com 25
```



----
[Connection timed out](https://talk.plesk.com/threads/postfix-smtp-connection-timed-out.354915/)

[Postfix server only attempts to connect on (blocked) port 25, not 587 as set in config](https://serverfault.com/questions/1005178/postfix-server-only-attempts-to-connect-on-blocked-port-25-not-587-as-set-in)


[Please stop recommending vultr, they won't unblock port 25 anymore.](https://github.com/LukeSmithxyz/emailwiz/issues/172)

```
sudo service postfix start
```
```
sudo service postfix stop
```
```
sudo service postfix restart
```
### To check if 25 port is blocked

```
telnet [domain] 25
```
```
sudo ufw allow out 25
```
```
sudo ufw allow 25
```
```
sudo ufw reload
```
