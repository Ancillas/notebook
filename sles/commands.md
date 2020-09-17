# Useful SLES Commands and Notes

## Zypper

### List available packages
`zypper search -s --details <package>`

### Zypper can cache files
`zyper -C /tmp/zypp/cache -d --dry-run <package>`

### Zypper can install CVE patches

Note: A zypper patch may close several CVE's.  It's usually easier to look for patches that could be installed rather than starting with a CVE.

#### List patches available for a CVE

`zypper lp --cve=CVE#`

#### Get information about a patch

`zypper info -t patch PatchName`

#### Install the patch using the CVE#

`zypper patch --cve=CVE#`

### Zypper Patch Commands

#### patch command to just download, but not install

`zypper patch -D -d —without-optional <patch name>-<patch version>`

## SLES Firewall

### Firewall - Allow SSH (useful when testing in VBOX)

Note: Will require sudo if you're not root.

```
firewall-cmd —permanent —zone=public —add-port=22/tcp
firewall-cmd —reload
