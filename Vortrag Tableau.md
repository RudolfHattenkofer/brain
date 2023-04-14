> Rudi from sell & pick introduces their company’s strategy for dashboard housekeeping and strengthening user engagement by analyzing Tableau Server Logs.

Agenda:
- Backup your server to an external repository

---

## Backup your repository to an external database
```
# Find path to pg_bin
export pg_bin=/opt/tableau/tableau_server/packages/pgsql.xxxxx.xx.xxxx.xxxx/bin

# Hack to allow us to log in with the superuser without a password. Set "tblwgadmin" from "md5" to "trust"
vi /var/opt/tableau/tableau_server/data/tabsvc/config/pgsql_0.xxxxx.xx.xxxx.xxxx/pg_hba.conf
host    all         tblwgadmin     127.0.0.1/32          md5
->
host    all         tblwgadmin     127.0.0.1/32          trust

# Reload server to pick up the changed config
su tableau
PGDATA=/var/opt/tableau/tableau_server/data/tabsvc/pgsql/data/ /opt/tableau/tableau_server/packages/pgsql.xxxxx.xx.xxxx.xxxx/bin/pg_ctl reload
exit

# Create backup
$pg_bin/pg_dump -d workgroup -h 127.0.0.1 -U tblwgadmin -p 8060 -f backup.sql -F p --no-acl --no-owner

# Take the backup.sql file and load it into your database!
```

---

## Schema
![[Screenshot 2023-04-14 at 15.47.56.png]]
```mermaid
graph TD;
	_sites --- _users
	_users --- group_users
	group_users --- _groups
	_users --- hist_users
	hist_users --- historical_events
	historical_events --- hist_views
	hist_views --- _views
	_views --- _workbooks
```
