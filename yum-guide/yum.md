# How to fix a few issues with YUM

tags: #yum #linux

## Fixing a failed wildfly-21 install
remove failed package
```console
yum --setopt=tsflags=noscripts remove <packagename>
````
