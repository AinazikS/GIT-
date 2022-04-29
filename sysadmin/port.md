# PORT GUIDE
[LINK](https://stackoverflow.com/questions/35868976/nginx-service-failed-because-the-control-process-exited)
```
sudo service nginx restart
```
```
nginx -t
```
```
sudo nano /var/log/nginx/error.log
```
```
2018/08/04 06:17:33 [emerg] 634#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
2018/08/04 06:17:33 [emerg] 634#0: bind() to [::]:80 failed (98: Address already in use)
2018/08/04 06:17:33 [emerg] 634#0: bind() to 0.0.0.0:80 failed (98: Address already in use)
```
>What the above error is telling is that it was not able to bind nginx to port 80 because it was already in use.
>To fix this, you need to run the following:
```
sudo apt install net-tools
```
```
sudo netstat -tulpn
```
Get the PID of the process that uses port 80 or 443. And send the kill command changing the <PID> value:
```
sudo kill -2 <PID>
```
Aternatively you can execute the following:
```
sudo fuser -k 80/tcp
sudo fuser -k 443/tcp
```
### Now that port 80 or 443 is clear, you can start Nginx by running the following:
```
sudo service nginx restart
```
```
sudo apt remove httpd httpd-devel httpd-manual httpd-tools mod_auth_kerb mod_auth_mysql mod_auth_pgsql mod_authz_ldap mod_dav_svn mod_dnssd mod_nss mod_perl mod_revocator mod_ssl mod_wsgi
```
___
```
sudo lsof -i -P -n | grep LISTEN
```
```
sudo netstat -tulpn | grep LISTEN

```  
  ```
  sudo lsof -i:22 # see a specific port such as 22
  ```
