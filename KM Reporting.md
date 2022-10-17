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


__Lösungsangebot sell & pick__:
- DATEV regelmäßiger Transfer der Daten
	- [DATEV Connect](https://www.datev.de/web/de/datev-shop/betriebliches-rechnungswesen/datevconnect/) -> Sehr dünn, nicht alle Daten, kein Support
	- DATEV Bot -> CSVs exportiert, z.B. täglich
- Haben sie mit Uknow schon versucht, alles in einem SQL Server, nur Mandant-seitig, nicht für Kanzlei -> Uknow ist sehr starr, nicht flexibel
- Whitelabel der Datenbasis oder sogar ganzes Cockpit
- Wollen selbst auch Änderungen machen (Due Dilligence etc)
	- Daten Stories zeigen?
	- Power Point für Reporting? -> Export Möglichkeiten
	- Rückfragen an Team oder Mandanten, Attachments? Kommentare, einbetten, ... -> Wie kann Tableau das abbilden? Automatische Dokumentation mit Anhängen "Datenraum" etc




__Nachgelagert:__
- ESG großes Thema -> Erstmal ausklammern
	- Wie ist das abzubilden außerhalb von DAX
	- Riesige Budgets

__Beteiligte:__
- Michael Baur, Burkom
	- Review IT Struktur
	- Dracoon DMS?