![Untitled (Draft)-1.jpeg](Webshop.assets/Untitled%20(Draft)-1.jpeg)

Hosting unter `<name>.ebke-cc21.hmcloudlabs.de`

# Infrastruktur

- Eine Code base, Hosting auf Gitlab
- Lambda für Hosting
   - 1 Funktion pro Endpunkt
   - ::Framework?:: [Getting started with Lambda - AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/getting-started.html) Flask etc, evtl Pyramid
   - Sprache: Python
   - Testing mit pytest etc
   - ::Frage: Rendering der HTML Seiten, Templates etc?::
- Datenbank für Order und Basket sind JSON Dateien in S3
   - Format:
      - `BUCKET_NAME/baskets/BASKET_ID`
      - `BUCKET_NAME/orders/ORDER_ID`
   - Zum Testing werden die Dateien einfach lokal abgelegt
   - \-> Parallele Zugriffe / Race conditions werden nicht erwartet, da die Order in der Regel nur von einem Nutzer gleichzeitig und seriell bearbeitet wird. Es wird viel Komplexität bla bla blub, Testing einfacher

# Codebase

- lib/
   - [store.py](http://store.py)
- [main.py](http://main.py)

# Module

## lib/store.py

```other
import os

local_mode = os.getenv("ENV") == "dev"

def read(path):
	if local_mode:
		content = open(path).read()
	else:
		content = s3.bucket(name).blob(path).read() # TODO

	return json.loads(content)

def store(path, content):
	data = json.dumps(content)
	if local_mode:
		open(path, 'w').write(data)
	else:
		s3.bucket(name).blob(path).write(data) # TODO

def get_order(order_id):
	read('orders/{}'.format(order_id))

def get_basket(basket_id):
	read('baskets/{}'.format(basket_id))

def store_order(order_id, content):
	store('orders/{}'.format(order_id), content)

def store_basket(basket_id, content):
	store('baskets/{}'.format(order_id), content)
```

# Endpunkte -> [main.py](http://main.py)

## / -> Index

Einstiegsseite. Es wird lediglich eine `basket_id` per UUID4 und umgeleitet auf `/products?basket_id=BASKET`

## /products

`basket_id` -> ID of our basket

- Zeigt Produkte mit ihrem Preis an
- Jedes Produkt hat einen "Kaufen" Button, der auf `modify_basket?product_id=PRODUCT&amount=1` umleitet

## /modify_basket

`basket_id` -> ID of basket to add the purchase to

`product_id` -> Name of product to purchase

`amount` -> Anzahl zum hinzufügen

- Legt das Produkt in den Basket, oder entfernt das Produkt wieder
- Leitet um auf `/products?basket_id=BASKET`

## /basket

`basket_id` -> ID of our basket

- Zeigt alle Produkte an
- Jedes Produkt hat einen "Entfernen" Button, der auf `modify_basket?product_id=PRODUCT&amount=-1` umleitet
- Es gibt einen "Checkout" Button, der auf `checkout?basket_id=BASKET` umleitet

## /checkout

`basket_id` -> ID of our basket

- Zeigt Übersicht mit allen Produkten an
- Zeigt ein Formular für CC + Adresse an
- Großer Button "Kaufen"

## /process_order

`basket_id` -> ID of our basket

- Erstellt aus dem Basket eine Order (Order ID per UUID4 generieren)
- Schickt Order mit `order_id` an CC Dienstleister
- Leitet um auf `wait_for_payment?order_id=ORDER`

## /wait_for_payment

`order_id` -> ID of our Order

- Checkt Status der `order_id` mit CC Dienstleister
- Wenn CC = pending, BITTE DAS FENSTER NICHT SCHLIESSEN

```other
<meta http-equiv="refresh" content="5" >
```

- Wenn CC = accepted, schickt Order mit `order_id` an Versandanbieter und leitet um zu `order_status?order_id=ORDER`
- Wenn CC = declined, leitet um zu `order_status?order_id=ORDER`

## /order_status

`order_id` -> ID of our Order

- Zeigt Bestellt-Status an:
   - CC declined -> Meldung
   - CC accepted -> Invoice URL
   - Historie des Versandanbieters
   - Inhalt der Bestellung

## /shipping_update -> BACKGROUND TASK

- Hört auf SNS Topic
- Schreibt `status` und `comment` aus dem SNS Event in `id` Order

## /manager

`secret_password` -> Password for managing interface

- Shows payments and purchased products

# Data format

## Order

```other
{
	"id": "ORDER_ID",
	"email": "kundenemail@hm.edu",
	"address": { "country": "GERMANY", "state": "", "city": "M¨unchen", "zip": "80335", "address1": "Johannes Ebke", "address2": "Lothstr. 34", "address3": "" },
	items": [{ "name": "Foo-Ding", "quantity": 4 }],
	"shipping": [
		{ "status": "sent", "comment": "wasauchimmer", "received_at": "2021-07-17" },
		{ "status": "delivered", "comment": "wasauchimmer", "received_at": "2021-07-17" },
	],
}
```



