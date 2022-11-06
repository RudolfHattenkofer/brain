[https://cloud.google.com/load-balancing/docs/https/setting-up-http-https-redirect](https://cloud.google.com/load-balancing/docs/https/setting-up-http-https-redirect)

The trick is to set up a new LB that has only a port 80 and redirects everything from HTTP to HTTPS. The original load balancer will only listen to 443.



