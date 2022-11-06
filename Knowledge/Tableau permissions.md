### Resources

Row level security: [Best Practices for Row Level Security - Tableau](https://help.tableau.com/current/server/en-us/rls_bestpractices.htm)

Whitepaper: [https://www.tableau.com/sites/default/files/whitepapers/tableau-rls-entitlement-tables_0.pdf](https://www.tableau.com/sites/default/files/whitepapers/tableau-rls-entitlement-tables_0.pdf)

### Concepts

`USERNAME()` function

Entitlement table

How to handle admins?

Extracts need special consideration - Relationships?

### Step by step

- Join entitlement data with data
- Filter with [User Functions](https://help.tableau.com/current/pro/desktop/en-us/functions_functions_user.htm#:~:text=Returns%20the%20username%20for%20the,for%20the%20Tableau%20Desktop%20user.)
   - `[Username] = USERNAME()`
- `ISMEMBEROF("Gruppe")`



