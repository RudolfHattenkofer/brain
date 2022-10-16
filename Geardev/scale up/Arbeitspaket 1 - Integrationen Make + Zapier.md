# Intro + Architektur

Unser Product verwendet im Backend Xano (Backend as a Service) und im Frontend (historisch) Worpress. Das Frontend kommuniziert via REST-API mit dem Backend. Die Integration in Worpress erfolgt über einen PlugIn-Mechanismus der React-Komponenten benutzt. Mein Ziel ist es eine möglichst seamless Customer-/Learner-Experience zu ermöglichen: Onboarding, Adoption, Rentention, Advocay.

Unser Produkt wird zum Einen Services zum Lernen der scale up Methode auf Basis eines Microlearning-Ansatzes gekoppelt mit dem Modell der 5 Moments of (Learning-)Needs anbieten. Zum Anderen werden wir Services (keine Tools) zur Anwendung unserer scale up Methode in den Teams, die wir betreuen, anbieten. Da unsere Tool sehr von Unternehmensdaten (KPIs) und anderen im Unternehmen genutzten Apps/Tools abhängig sind möchten wir eine gute Integration für unsere Kunden mit ihrer Infrastruktur anbieten, damit für sie Best of Breed möglich ist. In einem ersten Schritt möchten wir via der Integrationsplattformen Zapier und Make (früher Integromat) eine (bidirektionale) Anbindung an uns ermöglichen.

![PNG-Bild.png](PNG-Bild.png)

Deine Aufgabe für die nächsten zwei Wochen wäre zu recherchieren, was wir tun müssen, um eine solche Integration zu ermöglichen (Konzept, Architektur, Schnittstellen etc..) und einen kleinen Demonstrator zu erstellen. Ziel wäre es dabei so viel wie möglich zu verallgemeinern und so wenig wie möglich speziell für eine der beiden Integrationsplattformen zu implementieren. Von der Reihenfolge würden wir aber mit Make (Integromat) starten, da hier die Möglichkeit besteht, dass die Daten während des Transfers / der Verarbeitung in der EU verbleiben (DSGVO) und aus meiner Sicht die UI besser / einfacher ist.

Test-Szenario:

- Email entsprechen den Rohdaten, Postmark ist das Ursprungssystem
- Make/Zapier ist unser Gateway
- Daten sollen in der Xano App gespeichert werden

Architektur:

- Verbindung zum Ursprungssystem findet im Gateway statt
- Logik um aus den Rohdaten KPIs zu machen soll im Gateway definiert werden → Flexibilität
- Zugangsdaten für scale up werden ebenfalls im Gateway verankert

# Postmark setup

[Link to servers](https://account.postmarkapp.com/servers)

- Email [c958a2db17f5abf15ae86ac3b9f37c59@inbound.postmarkapp.com](c958a2db17f5abf15ae86ac3b9f37c59@inbound.postmarkapp.com)

# Make Integration

# Make

Temporär: Kunden bauen eigenen Make Flow, und schicken die Daten am Ende per Rest zu uns.

Final: Offizielle Integration für Make, die Kunden am Ende des Flows einstellen können. Das haben wir angefragt, aber von Make noch keine Antwort bekommen.

[Link to scenario](https://eu1.make.com/113313/scenarios/404772/edit)

### Schritt 1 - Test setup

Postmark receives incoming mail → Trigger Make → Write to Xano backend

![Image.png](zAssets/Image.png)

**Setup**:

- Incoming: Postmark - Watch Inbound Emails
- Transform: JSON - Create JSON
   - Add data structure
      - subject: Text
      - from: Text
      - body: Text, multi-line
   - Set up:
      - subject: Subject
      - from: From Name
      - body: Text Body
- Send: HTTP - Make a request
   - URL: [https://x8ki-letl-twmt.n7.xano.io/api:zhFYy16c/emails](https://x8ki-letl-twmt.n7.xano.io/api:zhFYy16c/emails)
   - Method: POST
   - Body type: Raw - JSON
   - Request content: JSON string

High level:

- Get data from source system
- Transform according to business logic in Make
- Build JSON object
- Send to scale up via HTTP API call

### Schritt 2

Mit Make sprechen und einen offiziellen Connector entwickeln. Das spart den Schritt, die Daten als JSON Objekt zu transformieren und den HTTP Connector selbst zu bauen, und. Stattdessen wählt man direkt im scale up Connector die Daten aus den vorherigen Schritten aus.

Damit neuer "High level flow":

- Get data from source system
- Transform according to business logic in Make
- Send to scale up Connector

Mockup:

![Image.png](zAssets/Image%20(2).png)

### Schritt 3

Im nächsten Schritt kann durch das Team eine Bibliothek aus Make Flows aufgebaut werden. Dadurch können Beispiele für einzelne Quellsysteme im scale up Frontend zur Verfügung gestellt werden. Dies senkt in der Zukunft die Barriere, um Systeme mit scale up zu verknüpfen.

# Zapier Integration

[Zapier Platform: Build one integration to connect with 3,000+ SaaS apps](https://zapier.com/platform)

![Image.png](zAssets/Image%20(3).png)

[Link to Zap](https://zapier.com/editor/162061221/published)

Setup:

- Create Postmark trigger and setup inbound webhook URL
- Setup Webhook with subject, from and body

![Screenshot 2022-07-16 at 21.31.29.png](Screenshot%202022-07-16%20at%2021.31.29.png)

# Xano setup

[Link to instance](https://x8ki-letl-twmt.n7.xano.io/admin/workspace/17608/dashboard)

- Create schema (emails table, from text, subject text, body text)
- POST [https://x8ki-letl-twmt.n7.xano.io/api:zhFYy16c/emails](https://x8ki-letl-twmt.n7.xano.io/api:zhFYy16c/emails)
- GET [https://x8ki-letl-twmt.n7.xano.io/api:zhFYy16c/emails](https://x8ki-letl-twmt.n7.xano.io/api:zhFYy16c/emails)

## Make

Pros:

- EU location
- Very flexible workflow builder
- Cheaper

Cons:

- Currently workaround with API due to manual approval process
- Playful UI
- Might need a full integration before a preview launch makes sense due to large setup overhead

## Zapier

Pros:

- Many many integrations
- Clean UI, easy guide right in the app, straightforward setup
- No need to create JSON objects, webhooks know JSON natively
- Might not even need a full integration for a preview launch

Cons:

- More expensive to run
- Mostly US region

