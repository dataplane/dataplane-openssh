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
