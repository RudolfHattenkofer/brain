```
from zeep import Client
client = Client("https://mobile-people.de/Service/API300.asmx?wsdl")
result = client.service.GetRevenue( Param="value", )
```



