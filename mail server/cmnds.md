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

### To check the logs journalctl -f | grep postfix
```
journalctl -f | grep postfix
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
