---
title: Google Tag Manager example
layout: belco
---

### Settings up Tag Manager

- Log in at https://tagmanager.google.com/ and go to your workspace.
- Go to **Variables** and create new custom variable
Use these settings:
**Name**:Belco *(The name is case sensitive)*
**Variable Type**: Data Layer Variable
**Data Variable Name**: belco
- Save the configuration

- Now create a new tag and name it Belco.
Use these settings:
**Name**: Belco
**Type**: Custom HTML
Paste the following code:
```html
<script>
!function(n,o){var e=window.belcoFunction||"Belco";window[e]||(window[e]=function(n){if(void 0===window[e][n])throw new Error("Unknown method");return window[e][n].apply(window[e],Array.prototype.slice.call(arguments,1))}),window[e]._q=[];for(var i=["init","sync","track","page","open","close","toggle","on","once","off","anonymousId","customer","reset","sendMessage"],t=function(n){return function(){var o=Array.prototype.slice.call(arguments);return o.unshift(n),window[e]._q.push(o),window[e]}},w=0;w<i.length;w++){var r=i[w];window[e][r]=t(r)}window[e].load=function(e){if(!n.getElementById("belco-js")){var i=n.createElement(o);i.async=!0,i.id="belco-js",i.type="text/javascript",i.src="//cdn.belco.io/v2/widget.js",i.onload=function(n){"function"==typeof e&&e(n)};var t=n.getElementsByTagName(o)[0];t.parentNode.insertBefore(i,t)}},window.belcoConfig&&window[e].load(function(){window[e]("init",window.belcoConfig)})}(document,"script");
</script>
<script>
  Belco.load(function() {
    var config = {{Belco}};
             
    if (config) {
      Belco.init(config)
    }
  })
</script>
```
  Note the {{Belco}} tag, there is the variable we just created.
  
- Add the **Page view** trigger to load the widget on page load.
- Save the new tag and head over to the next step.

...

### Using Data layers

If you haven't already, include the Google Tag Manager snippet in the <head> of your website.
  
We recommend adding the belco date layer variable before the Google Tag Manager snippet in order to have the variable available on page load.

Here is an example syncing the shopping cart contents.

For all available variables, please checkout our developer docs:
https://developers.belco.io/docs/javascript-client

```html
<head>
  <script>
    dataLayer = [{
      belco: {
        shopId: 'G4ag3eGyiKibrGcM7',
        cart: {
          items: [{
            id: 1,
            name: 'Product demo',
            quantity: 10,
            price: 12.34
          }],
          currency: 'EUR',
          total: 1234
        }
      }
    }];
  </script>

  <!-- Google Tag Manager -->
  <script>(function(w,d,s,l,i){w[l]=w[l]||[];w[l].push({'gtm.start':
  new Date().getTime(),event:'gtm.js'});var f=d.getElementsByTagName(s)[0],
  j=d.createElement(s),dl=l!='dataLayer'?'&l='+l:'';j.async=true;j.src=
  'https://www.googletagmanager.com/gtm.js?id='+i+dl;f.parentNode.insertBefore(j,f);
  })(window,document,'script','dataLayer','[Your GTM ID]');</script>
  <!-- End Google Tag Manager -->
</head>
```

...

### Support or Contact

Having trouble with the integration? Drop us a message, we're happy to help. 
