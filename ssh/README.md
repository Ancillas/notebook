# Useful SSH Info

## Basic SSH config

```
Host github.com
    HostName github.com
    Port 22
    User git
    IdentityFile ~/.ssh/id_rsa
```

## Save SSH key passphrase in MacOS keychain

```
Host github.com
    HostName github.com
    Port 22
    User git
    IdentityFile ~/.ssh/id_rsa
    AddKeysToAgent yes
    UseKeychain yes
```

## Match multiple host patterns

```
Host *-hostpattern-*.domain.com *-hostpattern-*
    User youruser
    LogLevel QUIET
```


## Don't Record Host Key

If you're working with an insecure host that gets rebuilt a lot with a new untrusted host key, you can avoid recording that host key to speed up development.

THIS IS NOT SECURE

```
Host *-your-pattern.domain.com
        StrictHostKeyChecking no
        UserKnownHostsFile /dev/null
        User foo
        LogLevel QUIET
```
