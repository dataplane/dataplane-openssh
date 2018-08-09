# dataplane-openssh
data plane patches to OpenSSH

+ password authentication disabled in source
+ password authentication attempts logged
+ client protocol and software version logging changed from debug() to logit()
+ client source address and source port included in password authentication logging
+ client source address and source port included in client protocol and software version logging

To apply a patch:

```
patch -p1 -d openssh-x.ypz/ < openssh-x.ypz.dataplane.patch
```

To create a patch:

```
diff -rupN openssh-x.ypz/ openssh-x.ypz.dataplane/ > openssh-x.ypz.dataplane.patch
```

## SSH protocol version 1

Support for SSH protocol version 1 was removed as of OpenSSH 7.6.  The
DataPlane.org patch associated with the auth1.c source file is therefore
no longer maintained.

## OpenSSL 1.1 and OpenSSH

Building OpenSSH with OpenSSL 1.1 is no longer supported due to
incompatibles between the two.  DataPlane.org is testing a build of the
dataplane-openssh patches in OpenSSH when built with LibreSSL.

While not perfectly clean and packaged, our test build process includes
the following steps:

* Build LibreSSL from source and install into the default directory prefix ```/usr/local```
* Add /usr/local/lib to /etc/ld.so.conf.d/local.conf and run ldconfig
* Setup OpenSSH build with ```LIBS=-lpthread ./configure --with-ssl-dir=/usr/local/lib```
