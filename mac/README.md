# Mac Notes

## Securely storing and retrieving environment variables

You can store secrets in your Mac keychain and then retrieve them in scripts.  This can be useful when seeding certain environment variables with secrets, like API keys.

### Writing the secret 

Disable history to avoid logging the secret.  In zsh this can be done by first running

```
fc -p
```

then

```
security add-generic-password -a "$USER" -s 'secret-name' -w 'secret-value'
# NOTE: $USER will be replaced with your username, which is what you want
```

### Reading the secret

```
security find-generic-password -a "$USER" -s 'secret-name' -w
# NOTE: $USER will be replaced with your username, which is what you want
```

### Putting it all together

Update your ~/.bash_profile (or whatever) file to set an environment variable using your secret

```
ENV_VAR_SECRET=$(security find-generic-password -a "$USER" -s "secret-value" -w)
```
