# Security

## New PHP version

```swift
apt-get update
apt-get install php7.3 php7.3-xml php7.3-mysql
service apache2 restart
```

## Wordfence

[wpexplorer.com/htaccess-wordpress-security/](http://wpexplorer.com/htaccess-wordpress-security/)

```swift
# wp-content/.htaccess
# Disable access to all file types except the following
Order deny,allow
Deny from all
<Files ~ ".(css|js|jpe?g|png|pdf|docx|.woff|.ttf|.svg|.gif)$">
Allow from all
</Files>
```

- Enable user locking
- Disable admin user
- Scan all paths

## Disable XMLRPC

```swift
<Files xmlrpc.php>
order deny,allow
deny from all
</Files>
```

## Security

```swift
# Deny access to wp-config.php file
<files wp-config.php>
order allow,deny
deny from all
</files>
```

## Disable file editing

```swift
# wp-config-php
define(‘DISALLOW_FILE_EDIT’, true);
```



