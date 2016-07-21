# Create an RPM for k8s

## Prerequisites

Download the tar files from github and place them in SOURCES.

### Download source

Example URLs:

```
wget https://github.com/kubernetes/kubernetes/archive/<commit>/kubernetes-<shortcommit>.tar.gz
wget https://github.com/kubernetes/contrib/archive/<commit>/contrib-<shortcommit>.tar.gz
```

Place them in `SOURCES`

### Get the right version of Go

I recommend using [gvm|https://github.com/moovweb/gvm]

For example, k8s 1.3.2 needs go1.6:

```
[root@host ~]# gvm install go1.4
Installing go1.4...
 * Compiling...
go1.4 successfully installed!
[root@host ~]# gvm use go1.4
Now using version go1.4
[root@host ~]# gvm install go1.6
Installing go1.6...
 * Compiling...
go1.6 successfully installed!
[root@host ~]# gvm use go1.6
Now using version go1.6
[root@host ~]# go version
go version go1.6 linux/amd64
```

## Building

Update the spec file (yes I could script this, but I haven't) to reference the correct commits

Then do:

```
rpmbuild -ba SPECS/kubernetes.spec
```
