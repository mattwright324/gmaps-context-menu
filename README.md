# gmaps-context-menu
Create context menus for Google Maps maps, markers, or shapes. Looks exactly like context menus in the current [Google Maps](https://www.google.com/maps).

![example comparison](https://i.imgur.com/6MjZ94m.png)

Simply add the css and js to your site and it is ready to go!

### Features
- Easily customizable
- Supports multiple context menus for different elements
- Looks almost exactly like Google Maps context menus
- Show or hide context menu items with a condition

```html
<link rel="stylesheet" href="css/gmaps-context-menu.css" />
<script type="text/javascript"  src="js/gmaps-context-menu.js"></script>
```

## Code examples

With your map and markers, circles, shapes...

```js
const map = new google.maps.Map(document.getElementById("map"), {
    zoom: 7,
    center: {lat: 40.697, lng: -74.259}
});
const circle = new google.maps.Circle({
    center: {lat: 40.697, lng: -74.259},
    strokeColor: "#00fff0",
    strokeOpacity: 0.5,
    strokeWeight: 2,
    fillColor: "#00fff0",
    fillOpacity: 0.15,
    radius: 10000
});
const marker = new google.maps.Marker({
    position: {lat: 40.697, lng: -74.259},
    draggable: true,
    optimized: false,
    zIndex: 99999999,
    showing: false
});
```

Use `gmaps-context-menu` to add the same context menu for all elements.

```js
const defaultContextMenu = new GmapsContextMenu(map, {
    options: [
        {
            text: "Move marker here",
            showWhen: function () {
                return true;
            },
            onclick: function (latLng) {
                // insert your code here
            }
        },
        {
            text: "Search here",
            showWhen: function () {
                return true;
            },
            onclick: function (latLng) {
                // insert your code here
            }
        }
    ]
});
defaultContextMenu.registerFor(circle);
defaultContextMenu.registerFor(marker);
```

Use `gmaps-context-menu` or make different context menus for different elements. If you don't register the context menu for a map element it will not appear on right click.

```js
const mapContextMenu = new GmapsContextMenu(map, {
    options: [
        {
            text: "Map option",
            showWhen: function () {
                return true;
            },
            onclick: function (latLng) {
                // insert your code here
            }
        }
});

const circleContextMenu = new GmapsContextMenu(map, {
    registerOpenForMap: false,
    options: [
        {
            text: "Circle option",
            showWhen: function () {
                return true;
            },
            onclick: function (latLng) {
                // insert your code here
            }
        }
});
circleContextMenu.registerFor(circle);

const markerContextMenu = new GmapsContextMenu(map, {
    registerOpenForMap: false,
    options: [
        {
            text: "Marker option",
            showWhen: function () {
                return true;
            },
            onclick: function (latLng) {
                // insert your code here
            }
        }
});
markerContextMenu.registerFor(marker);
```
