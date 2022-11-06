[Level of Detail Expressions - Tableau](https://help.tableau.com/current/pro/desktop/en-us/calculations_calculatedfields_lod.htm)

In Tableau, LODs are used to calculate values at a different level than what the visualization shows. They have special properties when used with aggregations: [Tableau LOD aggregations](./Tableau%20LOD%20aggregations.html)

There are four types of expressions: FIXED, INCLUDE, EXCLUDE and table scoped.

*FIXED* works with all data, split by the given dimensions. It is no affected by filters, only the “context”. See: [Tableau LODs and filters](./Tableau%20LODs%20and%20filters.html)

Limitations: Data sources with [Tableau Relationships](./Tableau.html) may not filter correctly this way.

*INCLUDE* returns the value for a given cell, but split by additional dimensions. It can again be further aggregated, e.g. to show the average sale per customer for a cell: `AVG({ INCLUDE [Customer Name] : SUM([Sales]) }`

*EXCLUDE* returns the value for a given cell, but excludes a dimension the view is split by. This enables the comparison with a total etc.

It is not possible to EXCLUDE a view filter this way.

*Table scoped* works with all data that is available for the table. It is the same as using FIXED without any dimensions.



