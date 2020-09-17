## Install without upgrading packages

Add these boot options

`manual=1 upgrade=0 self_update=0`

I also pressed F4 to ensure CD-ROM was set as a source, but I’m not sure if this is necessary.

## Configuring VMWare SLES VM to install packages from disk when install disk is in CD-ROM 1 and packages disk is in CD-ROM 2.

There’s probably no vim or nano, so you need to edit the repo config file in 
`/etc/zypp/repos.d`

For me it looked like this.

```
cp /etc/zypp/repos.d/SLES15-SP1-15.1-0.repo /root/SLES15-SP1-15.1-0.repo.bkp
cat /root/SLES15-SP1-15.1-0.repo.bkp | sed ’s;baseurl.*;baseurl=cd:///?devices=/dev/sr0,/dev/sr1;' > /root/SLES15-SP1-15.1-0.repo
mv /root/SLES15-SP1-15.1-0.repo /etc/zypp/repos.d/SLES15-SP1-15.1-0.repo
zypper modifyrepo -e 1
zypper refresh
zypper install vim
```

## Firewall - Open the SSH Port

No sudo required because you should be root at this point.

```
firewall-cmd —permanent —zone=public —add-port=22/tcp
firewall-cmd —reload
```

## Setting up a download test on a vanilla system

* Copy /etc/SUSEConnect.example to /etc/SUSEConnect and disable repo refresh on registration
* Use zypper to add the default repos/products from the upstream SLES repos
* Register the system with SUSEConnect
* Refresh the repos..
* Search for a patch using zypper to make sure they’re visible
* `zypper -C /root/packages/dir patch -d <patch>`
