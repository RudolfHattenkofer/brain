- Weiterleitung:
   - Wenn Learning journey → Lernen
   - Sonst: Anwenden
- Reihenfolge:
   - Lernen, Anwenden, Coachen
- Anwenden
   - Neuer Endpunkt: /tools
      - /tools/poll
      - /tools/bhag
   - Knopf "Umfragen", "BHAG", etc anzeigen
   - Wenn nur ein Produkt → Direkt anzeigen
   - Endvorstellung: Growth Canvas als Dashboard, momentan nur Links
- Fix "Berechtigungen"

Issues:

- Literally there is no "Lernen", "Coachen". It is not implemented, so no active checking/forwarding is possible.

Actions:

- Port to new create-react-app
- Create App and Embed versions
- Remove old JS-patterns (`bind(this)`, ...)
   - `bind(this)`
   - String concatenation
   - let → const
- Remove Redux
   - Inline all API calls to api.js inside of components
- Replace "blocks" with components
- Convert LESS to SCSS
- sessionStorage to localStorage (doesn't reset all the time)
- Start linting
- Function components instead of classes
   - useState for state
   - useEffect for initializers

