[Work with Log Files - Tableau](https://help.tableau.com/current/server-linux/en-us/logs_working_with.htm)

[Server Log File Locations in the Ziplog Archive - Tableau](https://help.tableau.com/current/server-linux/en-us/logs_loc.htm)

Web server:

```other
tail -f /var/opt/tableau/tableau_server/data/tabsvc/logs/httpd/access.2020_08_25_00_00_00.log
```

Script logs:

```other
/var/opt/tableau/tableau_server/data/tabsvc/logs/
```

Controller logs:

```other
cd /var/opt/tableau/tableau_server/data/tabsvc/logs/tabadmincontroller/
tail -f tabadmincontroller_node1-0.log
```



