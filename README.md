mod_remoteip patch for scheme support
=====================================

This patch provides support for the https scheme in apache if set by a reverse proxy.

Configuration
-------------

The patch adds one configuration parameter to the mod_remoteip module.

##### RemoteIPProtoHeader

Common headers set by the ssl proxy are the following

* Front-End-Https
* X-Forwarded-Proto

The header has to be "On" or "https".

A complete configuration line looks like this

```apacheconfig
RemoteIPProtoHeader Front-End-Https
```

Implementation notes
-------------------

This patch respects the RemoteIP Proxy restrictions. So only an authorized proxy/client can set the scheme to https.

Usage
-----

We only provide a patch and the complete mod_remoteip.c file for replacement.   
You have to patch the apache source and compile to to get this to work.  

If enough intrerest exists its possible to provide a standalone module with precompiled binaries.
-------------------------------------------------------------------------------------------------

## Cloudflare Configuration - Show Actual IPs in Logs and Applications this is an Apache2 module.
## To Enable mod_remoteip
LoadModule remoteip_module modules/mod_remoteip.so
RemoteIPHeader X-Forwarded-For
RemoteIPTrustedProxy 173.245.48.0/20
RemoteIPTrustedProxy 103.21.244.0/22
RemoteIPTrustedProxy 103.22.200.0/22
RemoteIPTrustedProxy 103.31.4.0/22
RemoteIPTrustedProxy 141.101.64.0/18
RemoteIPTrustedProxy 108.162.192.0/18
RemoteIPTrustedProxy 190.93.240.0/20
RemoteIPTrustedProxy 188.114.96.0/20
RemoteIPTrustedProxy 197.234.240.0/22
RemoteIPTrustedProxy 198.41.128.0/17
RemoteIPTrustedProxy 162.158.0.0/15
RemoteIPTrustedProxy 104.16.0.0/12
RemoteIPTrustedProxy 172.64.0.0/13
RemoteIPTrustedProxy 131.0.72.0/22
RemoteIPTrustedProxy 2400:cb00::/32
RemoteIPTrustedProxy 2606:4700::/32
RemoteIPTrustedProxy 2803:f800::/32
RemoteIPTrustedProxy 2405:b500::/32
RemoteIPTrustedProxy 2405:8100::/32
RemoteIPTrustedProxy 2a06:98c0::/29
RemoteIPTrustedProxy 2c0f:f248::/32

#### i put this (mod_remoteip.conf) in ->  /etc/httpd/conf.modules.d
#### and i was successful with ->  RemoteIPHeader X-Forwarded-For
##### If that doesn't work you could try -> RemoteIPHeader CF-Connecting-IP


LICENSE
-------

Apache License Version 2.0.  
Please see the file called LICENSE.
