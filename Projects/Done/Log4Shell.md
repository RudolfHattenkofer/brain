4Shell

Vulnerability that exploits log4j.

[Initial post by LunaSec](https://www.lunasec.io/docs/blog/log4j-zero-day/)

[Details by Cloudflare](https://blog.cloudflare.com/inside-the-log4j2-vulnerability-cve-2021-44228/)

[Mitigation Guide](https://www.lunasec.io/docs/blog/log4j-zero-day-mitigation-guide/)

[Exploit example](https://github.com/tangxiaofeng7/CVE-2021-44228-Apache-Log4j-Rce)

[BSI Notice](https://www.bsi.bund.de/SharedDocs/Cybersicherheitswarnungen/DE/2021/2021-549032-10F2.pdf?__blob=publicationFile&v=3)

[List of Software](https://gist.github.com/SwitHak/b66db3a06c2955a9cb71a8718970c592) * [Salesforce](https://status.salesforce.com/generalmessages/826) * [Unifi](https://community.ui.com/releases/UniFi-Network-Application-6-5-54/d717f241-48bb-4979-8b10-99db36ddabe1) *

[Apache Log4j2 vulnerability (Log4shell) | Tableau Software](https://kb.tableau.com/articles/issue/Apache-Log4j2-vulnerability-Log4shell?utm_campaign=2020225_EGCustService_TRANS_USCA_en-US_2021-12-15_T1-log4j_update&utm_medium=Email&utm_source=Eloqua&domain=sell-pick.com&eid=CTBLS000014136073&elqTrackId=4489b8d324b14d25adfa0356b5546712&elq=40618ef82b154c208fd7ea7f7c3f63b2&elqaid=53231&elqat=1&elqCampaignId=52414)

```other
/opt/tableau/tableau_server/packages/scripts.20213.21.0902.2150/stop-admi
nistrative-services
sudo su -l tableau
echo LOG4J_FORMAT_MSG_NO_LOOKUPS=true >> ~/.config/systemd/tableau_server.conf.d/log4j.conf
exit
/opt/tableau/tableau_server/packages/scripts.20213.21.0902.2150/start-administrative-services
```

\-> Enabled WAF

\-> Disabled LDAP completely



