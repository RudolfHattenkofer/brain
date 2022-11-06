# 2020-12-29 Slider lazysizes

- [x] Lazy load doesn't actually show low Q image after the very first one. (load the page then drop your network speed, you'll see the svg loads in network tab and the photographers are rotating but the image does not)
- [x] Lazy load component never shows the placeholder image for the first seconds while waiting for fetch featured photographers
- [x] can you add a callback to the lazyimage component that tells the slider not to change until the image is loaded?

[Test](http://localhost:3002/marketplace)

[Docs](https://github.com/aFarkas/lazysizes/tree/master/plugins/blur-up)



