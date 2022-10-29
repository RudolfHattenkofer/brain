Marketing: HomeController vs Marketplace

[clients.remarkvisions.com](http://clients.remarkvisions.com/) only listings_path (old one)

## Routes

- `post ‘:slug’, to: 'public#contact’`
- `get “:url”, to: "application#render_404`
- `mount Homesnap::Base => '/'`
- `root to: ‘marketing/home#index'`
- Investigate defaults

Both fine, they still need some text to match

- Investigate `Homesnap::Base`
   - API for something?
   - Swagger, so probably scoped properly

Ignore

- Investigate `Marketing::HomeController#index`
   - See below

## `redirect_user`

```swift
# This will only match if you are on a special path
@listing = Listing.by_host request.host

# This is for custom domains
if @listing
  redirect_to gallery_path

# This checks for clients.remarkvisions.com
elsif remark_visions?
  # Old design for listings_path
  redirect_to listings_path

# This has scheduler logic
elsif should_go_to_scheduler?
  redirect_to scheduler_dashboard_path

# Logged in
elsif current_user && current_user.listings.count > 0
    # Redirect to listings, koaware.com gets new_design
  redirect_to_listings_path

# Default!
else
  redirect_to marketing_marketplace_path
end
```

## What did Alex change?

*Current behaviour*

- listings_path for logged in and [clients.remarkvisions.com](http://clients.remarkvisions.com/)
- Anonymous gets marketing*marketplace*path

*Desired behaviour?*

Do you want the `MarketplaceController` to instead of the `HomeController`?

An easier solution would be to just move the index files to the HomeController, so we don’t mess with any of the existing redirects. This would also be a little cleaner imho, since the `HomeController` handles exactly one thing: Showing the home page. It will just redirect a couple of special cases (remark koaware etc), but then it shows the home page again.



