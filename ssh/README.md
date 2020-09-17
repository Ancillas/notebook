# Useful SSH Info

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
