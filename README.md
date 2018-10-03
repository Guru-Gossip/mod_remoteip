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

LICENSE
-------

Apache License Version 2.0.  
Please see the file called LICENSE.
