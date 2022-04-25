# Apt-key Error
```
sudo apt-key list
```
Example: pub   rsa2048 2011-08-19 [SC] [expires: 2024-06-14] 
               573B FD6B 3D8F BC64 1079  A6AB ABF5 BD82 7BD9 BF62
         uid           [ unknown] nginx signing key <signing-key@nginx.com>
         

```
sudo apt-key del 7BD9BF62
```
Copy last 2 XXXX  XXXX symbols there and join them 

