

```other
gcloud beta compute security-policies rules create 49 \ 
     --security-policy=block-wp \
     --action "rate-based-ban" \
     --rate-limit-threshold-count=10 \
     --rate-limit-threshold-interval-sec=60 \
     --ban-duration-sec=3600 \
     --ban-threshold-count=10 \
     --ban-threshold-interval-sec=60 \
     --conform-action=allow \
     --exceed-action=deny-403 \
     --enforce-on-key=IP \
     --expression "request.path.matches('/wp-includes/|.php|.asp|.xml|.env|.git')" \
     --project koaware-prod
￼
gcloud beta compute security-policies rules update 50 \
     --security-policy=block-wp \
     --action "rate-based-ban" \
     --rate-limit-threshold-count=200 \
     --rate-limit-threshold-interval-sec=60 \
     --ban-duration-sec=3600 \
     --ban-threshold-count=100 \
     --ban-threshold-interval-sec=60 \
     --conform-action=allow \
     --exceed-action=deny-403 \
     --enforce-on-key=IP \
     --src-ip-ranges "0.0.0.0/0" \                                                  
     --project koaware-prod

gcloud beta compute security-policies rules update 51 \
     --security-policy=block-wp \
     --action "rate-based-ban" \
     --rate-limit-threshold-count=20 \
     --rate-limit-threshold-interval-sec=60 \
     --ban-duration-sec=3600 \
     --ban-threshold-count=100 \
     --ban-threshold-interval-sec=60 \
     --conform-action=allow \
     --exceed-action=deny-403 \
     --enforce-on-key=IP \
     --expression "request.path.matches('^/$|^/gallery$|^$')" \
     --project koaware-prod
```

