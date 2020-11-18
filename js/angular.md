# Angular

## Example project structure (munimap)

* static/js: Controller code (goes to static/dist via webpack)
* templates/munimap
* templates/munimap/macros


```html
<div anol-layerswitcher 
      remove-layer-enabled=removeLayerEnabled 
      template-url="munimap/layerswitcher-overlays.html" class="overlay-layerswitcher"></div>
```

-> layerswitcher-directive.js

* Directives

<script type="text/ng-template" id="munimap/layerswitcher-overlays.html">