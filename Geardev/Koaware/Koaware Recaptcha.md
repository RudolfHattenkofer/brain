Resources:

[https://developers.google.com/recaptcha/docs/verify#api-response](https://developers.google.com/recaptcha/docs/verify#api-response)

[Adding reCaptcha v3 to a Rails app without a gem](https://dev.to/morinoko/adding-recaptcha-v3-to-a-rails-app-without-a-gem-46jj)

## Status Quo

### Where is the captcha used?

[https://github.com/Koaware/koaware/search?q=captcha&unscoped_q=captcha](https://github.com/Koaware/koaware/search?q=captcha&unscoped_q=captcha)

- [https://github.com/Koaware/koaware/blob/b8221ba21a25720e7b823cb1852cf54ab8778839/app/views/public/contact.html.erb](https://github.com/Koaware/koaware/blob/b8221ba21a25720e7b823cb1852cf54ab8778839/app/views/public/contact.html.erb)
- [https://github.com/Koaware/koaware/blob/736d74d49a2b4433ee5a0b489547e3f9304ffed8/app/views/public/contact2.html.erb](https://github.com/Koaware/koaware/blob/736d74d49a2b4433ee5a0b489547e3f9304ffed8/app/views/public/contact2.html.erb)
- [https://github.com/Koaware/koaware/blob/b9e18388531aec0f8492619978bde97b418e5453/app/views/layouts/property_website_templates/salt_creek/index.html.haml](https://github.com/Koaware/koaware/blob/b9e18388531aec0f8492619978bde97b418e5453/app/views/layouts/property_website_templates/salt_creek/index.html.haml)

### What captcha solution is currently in use?

Invisiblecaptcha, not effective anymore, lots of spam

## Recaptcha v3

### Do Domains have to be verified?

No, you can just add them.

Actually, verification can be disabled entirely. [Domain Validation](https://developers.google.com/recaptcha/docs/domain_validation)

The domain should just be checked against the valid domains in the database to comply with the terms of use.

### How to add to Rails

[reCAPTCHA v3 Ruby on Rails gem](https://github.com/igorkasyanchuk/new_google_recaptcha)

The gem definitely looks like a good option!

The DIY solution you provided above seems to do exactly the same, the code for the view is copy/pasted from the gem here: [new_google_recaptcha/view_ext.rb](https://github.com/igorkasyanchuk/new_google_recaptcha/blob/master/lib/new_google_recaptcha/view_ext.rb)

The verification code is also collected from throughout the gem. I would not bother recreating this and just follow the instructions in the gem readme!

## implement

validator =

NewGoogleRecaptcha::Validator.new(

token: token,

action: action,

minimum*score: minimum*score

)

is_valid = validator.call



