## Is everything up to date?

```sql
brew install mysql-client
```

Update brew openssl, brew mysql-client and the mysqlclient pip package.

## Still trouble? Try some of these:

```swift
brew info openssl

# Add to .config/fish/config.fish
set PATH /usr/local/opt/openssl@1.1/bin $PATH
set -x LDFLAGS "-I/usr/local/opt/openssl/include -L/usr/local/opt/openssl/lib"
set -x PIPENV_TIMEOUT 9999
```



