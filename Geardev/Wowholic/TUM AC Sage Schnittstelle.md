Pfad: `mtm-tum-crm-event`

Fehler: `loader.php:1354`

- Method is called like a static method, but it expects to be within an instantiated object
- Maybe there was a change in the Wordpress API?
- Fix: `add_filter('rewrite_rules_array', array($this, 'my_insert_rewrite_rules'));`> `add_filter('rewrite_rules_array', array(self, 'my_insert_rewrite_rules’));`
- Brief fixed plugin code
- Lots of static rewrites, link to relevant sections
   - see `loader.php#my_insert_rewrite_rules`
   - [Veranstaltungen](https://beta.together.tum.de/veranstaltungen)
   - [Events](https://beta.together.tum.de/events/)
- Layout and styles are completely fixed
   - see: `wp-content/plugins/mtm-tum-crm-event/includes/templates/`
- Connection to data
   - SOAP, see `includes/CommunityService.class.php`
   - Login and password are hardcoded in code
   - “Comment out in Production”

Commented out now, why is this a thing??

- FRAGE: Im Code wird “MTM*WSDL*URL” verwendet, aber nie definiert. Auf was muss diese gesetzt werden?
   - wp-config.php
   - `define('MTM_WSDL_URL', 'https://www.crm.tum.de:8001/CommunityService/?wsdl');`
- FRAGE: Gibt es außer “Comment out in Production” und “MTM*WSDL*URL” noch andere Anpassungen, die für den Live Betrieb vorgenommen werden müssen? Bekommen wir Zugriff auf die Live Version des Codes?

## Filter events?

```swift
Tum_Crm_Events::get_data_by_count(0, get_query_var('eventkat'))

in loader.php
public static function get_data_by_count
```

## Test

[https://beta.together.tum.de/veranstaltungen/](https://beta.together.tum.de/veranstaltungen/)



