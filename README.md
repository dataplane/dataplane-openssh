# dataplane-openssh
data plane patches to OpenSSH

+ password authentication disabled in source
+ password authentication attempts logged
+ client protocol and software version logging changed from debug() to logit()
+ client source address and source port included in password authentication logging
+ client source address and source port included in client protocol and software version logging

To apply a patch:

  patch -p1 -d openssh-x.ypz/ < openssh-x.ypz.dataplane.patch
