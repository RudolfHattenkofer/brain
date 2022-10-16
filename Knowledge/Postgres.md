[earthdistance](https://www.postgresql.org/docs/9.6/earthdistance.html)

`earth_box` makes a box around a point, you can then check if a point is within that box:

```other
earth_box(center, distance) @> point
```



