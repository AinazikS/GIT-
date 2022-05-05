# Apt-key ~~Error~~

```
sudo apt-get update
```
>Output:  
   Err:3 http://nl.clouds.archive.ubuntu.com/ubuntu impish InRelease                              
   The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 871920D1991BC93C
   Hit:5 http://apt.vestacp.com/impish impish InRelease                           
   Err:5 http://apt.vestacp.com/impish impish InRelease                           
   The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 42C5B2130A1F7714
   Get:6 http://nl.clouds.archive.ubuntu.com/ubuntu impish-updates InRelease [115 kB]
   Err:4 http://security.ubuntu.com/ubuntu impish-security InRelease 
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 
```
>__At the and of the line add the number that were provided in the Output. Example: 42C5B2130A1F7714__
