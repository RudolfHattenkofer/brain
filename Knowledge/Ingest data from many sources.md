Pulling data from many sources is a challenge, both operationally and from an engineering aspect.

Ingestion method (HTTP, FTP, custom protocol), data format (JSON, XML, GraphQL, text, binary) and schema are different for every provider. There is no unified way to pull data from sources. CDC (change data capture or other delta updates) is not always available.

At the same time providers or single tenants within a provider can have outages (downtime, maintenance, expired credentials) or deliver invalid data (format changed, configuration error). This poses a significant operational challenge for monitoring and communication to the end user.

There are many similar solutions out there, but most of them have connectors for e-commerce or existing BI sources, not individual services a corporation might use. This is especially true for niche or upcoming segments like restaurants. Significant engineering resources are required to adapt to new services.

Further reading:

[[Data Pipeline]]

[[Data Ingestion]]

