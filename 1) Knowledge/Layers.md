One if the guiding principles that is often talked about and has many names, e.g.:

- Layers
- Onion
- Hexagonal architecture

The main idea is the *separation of concerns through layers*, which may include:

- Infrasctructure
   - Database abstractions
   - Gateways to external services
- Various layers of business logic
   - PORO (Ruby)
   - Umbrella applications (Elixir)
- User facing application
   - Actual UI for end users
   - Batch job
   - Public API
   - Private API

Every layer should only be concerned with relevant logic and should not leak (opaque implementation). Higher layers do not know how lower layers operate. Lower layers do not know of the existence of higher layers and never call “up”. Only data can be passed up.



