---
client: Kreitinger Maierhofer
date: 2022-10-17
tags: meeting
---
__Kontext:__
- Finanzzahlen aus DATEV auswerten
	- mit anderen Daten anreichern: Personio, ...
- Features
	- Forecast
	- Budgetierung
	- Soll vs Ist, Ursachenforschung
	- KPIs
- Zielgruppen
	- Mandanten
		- Eigene Lösung: Uknow
		- Weniger komplex als Kanzleien, nur Financials
		- G&V, Lohn
		- Wie sieht eine allgemeine Lösung für alle Mandanten aus?
			- Rollen-fokussiert:
				- CFO, Investor:in
				- PE periodische Berichte
					- Paginieren: "Freeze" der Daten, damit sie interpretiert werden können
					- K&M möchte vor-interpretieren, damit Interims-CFO Arbeit von CFO für mehrere Unternehmen machen kann -> PE glücklich "CFO/Finance as a Service"
	- Kanzleien
		- Ist auch ERP System (Zeiterfassung etc)
		- In DATEV keine Möglichkeiten zur Auswertung
		- Schlechte Drittanbieter für zu viel Geld (z.B. Datamaster von [Bissantz](https://www.bissantz.de/en/))
		- Eigene KPIs sind klar
			- CSV -> Verzeichnis -> Power BI)
			- Monatlich -> Ziel täglich
			- Insbesondere Zeiterfassung
			- Klassisch: Alerting, Subscriptions, ...
			- Buchungssätze (Prozent Automatisierung)
			- Anzahl Personalabrechnungen, ...
		- Gruppen
			- Mandatsverwantwortung für einzelne Mandaten
			- Mentee + Mentoring (keine Zeit aufgezeichnet etc)
- Andere Tools
	- [LucaNet](https://www.lucanet.com/)
	- [U-Know](https://www.u-know.eu/)
		- Entwickelt von: [Dieter Steiner](https://www.northdata.com/Steiner,+Dieter,+Regensburg/vef) 


__Lösungsangebot sell & pick__:
- DATEV regelmäßiger Transfer der Daten
	- [DATEV Connect](https://www.datev.de/web/de/datev-shop/betriebliches-rechnungswesen/datevconnect/) -> Sehr dünn, nicht alle Daten, kein Support
	- DATEV Bot -> CSVs exportiert, z.B. täglich
	- BWA, Bilanz?
- Whitelabel der Datenbasis oder sogar ganzes Cockpit
	- Haben sie mit Uknow schon versucht, alles in einem SQL Server, nur Mandant-seitig, nicht für Kanzlei -> Uknow ist sehr starr, nicht flexibel
- Wollen selbst auch Änderungen machen (Due Dilligence etc)
	- Daten Stories zeigen?
	- Power Point für Reporting? -> Export Möglichkeiten
	- Rückfragen an Team oder Mandanten, Attachments? Kommentare, einbetten, ... -> Wie kann Tableau das abbilden? Automatische Dokumentation mit Anhängen "Datenraum" etc
- 4-Augen-Prinzip Review
	- Über alle Mandate hinweg KPIs checken: BWA Positionen überprüfen, Monatsschwankungen etc
	- Guter Einstieg für Kanzleien, weil direkte Arbeitsersparnis
- Rohdaten direkt sehen ist sehr wichtig: Buchungen ist kleinste Ebene
	- Direkt Effekte sehen, Probleme identifizieren
	- Kann man Einmaleffekte etc direkt annotieren? "EBITDA runtergegangen, weil einmalig hohe Bewirtungskosten durch Oktoberfest" -> Nicht Tool wechseln
- Business Case
	- Einmalig + Lizenzen
	- Was ist ein Standort?
	- Enterprise + Masse -> Muss sich natürlich auch rechnen
- Datenpunkte
	- Status Quo: P&L / BWA
	- Mehrwert: Bilanz + Lohn

- Next steps
	- Mandantensicht
		- Beispiel-Mandant suchen
	- Evaluierung Datentransfer
		- Wie war es bei U-Know?
		- Wie funktioniert der automatisierte Transfer?
	- Baby steps!
		- Wieder super sauberes Projektmanagement
		- Erreichbare Schritte
		- Wirklich mal U-Know unter die Lupe nehmen
	- Erste Ziele:
		- Kleiner Wow-Effekt
		- Nutzungsrate durch Personal der Kanzlei -> Change Management
		- Daten automatisch DATEV raus
		- Belegbilder mit rein!





__Nachgelagert:__
- ESG großes Thema -> Erstmal ausklammern
	- Wie ist das abzubilden außerhalb von DAX
	- Riesige Budgets

__Beteiligte:__
- Michael Baur, Burkom?
	- Review IT Struktur
	- Dracoon DMS?