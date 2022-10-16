[scale up Dashboard](https://www.scaleup.de/dashboard/)

[Zapier Integration](https://developer.zapier.com/app/166295/version/1.0.0)

## API

[Toolset API](https://api.scaleup.de/api:sVzRHGGB)

- # KPI: kpis
```plaintext
id: integer
created_at: timestamp
changed_at: timestamp
account_id: integer
title: text
value: decimal
unit: text
type: enum
intervall: enum
active: bool
```

- # KPI Werte: kpi_values
```plaintext
id: integer
created_at: timestamp
kpi_id: integer
account_id: integer
value: decimal
```

- # Ziel: kpi_goal

```plaintext
id: integer
created_at: timestamp
account_id: integer
kpi_id: integer
title: text
description: text
start_at: date
end_at: date
value: decimal
```

[Auth API](https://api.scaleup.de/api:nNrRBg3S)

- /auth/login
- /auth/me
- Keine Zugänge anlegen!

# Gedanken zu API Features

Actions:

- Aktuellen Wert für KPI setzten //request: name, value
- Aktuellen Wert des KPI lesen //request: name
- Letzte 100 Werte des KPIs lesen //request:  name; response [{value, date}]
- Werte des KPI aus dem Zeitraum Startdatum bis Enddatum lesen //request: name, start_date, end_date; response [{value, date}]

Events:

- Wert eines KPI hat sich geändert //response: name, value
- KPI Zielwert wurde erreicht //response: name, value, kpi_goal_title, kpi_goal_value

