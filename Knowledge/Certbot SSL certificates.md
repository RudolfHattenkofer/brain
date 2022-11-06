```swift
# Renewal
certbot renew

# Add new
certbot -d domain.com
```

## Add certificate to Froxlor

```swift
# Own vHost settings
SSLCertificateFile /etc/letsencrypt/live/domain.com/cert.pem
SSLCertificateKeyFile /etc/letsencrypt/live/domain.com/privkey.pem
SSLCertificateChainFile /etc/letsencrypt/live/domain.com/chain.pem
```



