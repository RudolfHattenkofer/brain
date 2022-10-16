How does the database connection pool work? Our main concern is disconnecting when no requests have been made in a while.

## Ecto.Repo

This module handles everything and is the entrypoint for the config in our app.

[https://hexdocs.pm/ecto/Ecto.Repo.html](https://hexdocs.pm/ecto/Ecto.Repo.html)

## Ecto.Adapters.Postgres

Handles Postgres databases specifically.

[Ecto.Adapters.Postgres — Ecto SQL v3.2.0](https://hexdocs.pm/ecto_sql/Ecto.Adapters.Postgres.html)

## DBConnection.ConnectionPool

This module is used to manage a pool of connections for use by many processes.

[DBConnection.ConnectionPool – db_connection v2.0.2](https://hexdocs.pm/db_connection/2.0.2/DBConnection.ConnectionPool.html)

[GitHub - elixir-ecto/db_connection: Database connection behaviour](https://github.com/elixir-ecto/db_connection)

[DBConnection — db_connection v2.1.0](https://hexdocs.pm/db_connection/2.1.0/DBConnection.html#start_link/2)

`idle_interval` merely pings the database so the connection doesn't drop.

## Summary

There does not seem to be an easy way to set this behaviour



