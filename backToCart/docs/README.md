# Back to Cart

## What it does

This plugin retrieves the list of layer keys from RAMP and uses a URL template to redirect the browser to a different page along with the keys.

When a url is registered, a button is added to the side menu in RAMP.

## Scripts

Both the `legacy-api.js` script from RAMP and `backToCart.js` for this plugin must be present. Load them in the order: `backToCart.js` -> `legacy-api.js` -> `rv-main.js`. All of this must be done before attempting to set the catalogue URL (detailed below).

## Setting the catalogue URL

To set the catalogue URL, call `backToCart.setCatalogueUrl` with the map's id and the url. Use the placeholder `{RV_LAYER_LIST}` where the layer keys should go.

This should be called within a callback on the `mapAdded` observable:

```
RZ.mapAdded.subscribe(function(mapi) {
    backToCart.setCatalogueUrl('sample-map', 'www.example.com?keys={RV_LAYER_LIST}');
});
```
