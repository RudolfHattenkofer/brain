# 2021-01-12 Distances

```other
SELECT display, photographer_surcharge_travel_distance FROM "bookings_photographer_applications" INNER JOIN "users" ON "users"."id" = "bookings_photographer_applications"."user_id" INNER JOIN "addresses" ON "addresses"."addressable_id" = "users"."id" AND "addresses"."addressable_type" = 'User' WHERE 
(

(photographer_willing_to_surchage_travel is true and earth_box(ll_to_earth(lat, lng), 1609 * photographer_surcharge_travel_distance) @> ll_to_earth(33.815305, -81.104235))
 or
(photographer_willing_to_surchage_travel is false and earth_box(ll_to_earth(lat, lng), 1609 * photographer_base_travel_distance) @> ll_to_earth(33.815305, -81.104235))
)

order by display
```

photographers_controller

available_photographer_finder



