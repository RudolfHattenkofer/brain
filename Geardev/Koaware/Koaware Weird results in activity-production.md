[https://koaware.com/scheduler/search/new?address=123+North+Main+Street%2C+Alpharetta%2C+GA%2C+USA&listing_price=239021&square_feet=1899&service_ids=130&coupon_code=FB20&fbclid=IwAR2CEHZeFKCYvKm_rzGHQq-ISv8NEvZH43d5tLsU4T95isfvhmaobQ59SBo](https://koaware.com/scheduler/search/new?address=123+North+Main+Street%2C+Alpharetta%2C+GA%2C+USA&listing_price=239021&square_feet=1899&service_ids=130&coupon_code=FB20&fbclid=IwAR2CEHZeFKCYvKm_rzGHQq-ISv8NEvZH43d5tLsU4T95isfvhmaobQ59SBo)

When is this event created?

`[PhotographersController#track_analytics](https://github.com/Koaware/koaware/blob/master/app/controllers/scheduler/api/photographers_controller.rb)`

Route: scheduler/api/photographers

[Recent calls](https://console.cloud.google.com/logs/viewer?project=koaware-prod&folder&organizationId&minLogLevel=0&expandAll=false&interval=PT1H&resource=http_load_balancer&advancedFilter=resource.type%3D%22http_load_balancer%22%0AhttpRequest.requestUrl:%22scheduler%2Fapi%2Fphotographers%22)

```swift
3:39pm CET - 96.83.17.33 - “GET https://koaware.com/scheduler/api/photographers?service_ids=130&address=123%20North%20Main%20Street,%20Alpharetta,%20GA,%20USA&start_date=Wed%20Oct%2009%202019%2010:00:00%20GMT-0400%20(EDT)&end_date=Tue%20Oct%2015%202019%2023:59:59%20GMT-0400%20(EDT)&square_feet=1899&listing_price=249000” 200 38300 “https://koaware.com/scheduler/search/new?address=123+North+Main+Street%2C+Alpharetta%2C+GA%2C+USA&listing_price=249000&square_feet=1899&service_ids=130” “Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_5) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/12.1.1 Safari/605.1.15”`
```

Address 96.83.17.33 is from Comcast in Georgia

After further research, it turns out that most of these are not from Google but instead from actual users.



