# Znaczniki | Markers Google Maps JavaScript API
Jak ustawić znacznik w Google Maps? Mapa Google z własnym znacznikiem z ikoną z pliku .png oraz wyskakującym okienkiem w html. Prosta mapa google.

## Url

```sh
https://raw.githubusercontent.com/atomjoy/marker/main/google-marker.png
```

## Sample map

- <https://developers.google.com/maps/documentation/javascript/examples/marker-simple>
- <https://developers.google.com/maps/documentation/javascript/markers?hl=pl>
- <https://spatialized.io/advanced-google-maps-markers-definitive-guide-94c5a070615e436ab0a255b9f5100a88>

```html
<html>
	<head>
		<title>Simple Map</title>
		<!-- Old google map -->
		<script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyB41DRUbKWJHPxaFjMAwdrzWzbVKartNGg&callback=initMap&v=weekly" defer></script>

		<!-- <link rel="stylesheet" type="text/css" href="./style.css" />
		<script type="module" src="./index.js"></script> -->

		<script>
			// Map
			let map = null
			// Google map
			function initMap() {
				map = new google.maps.Map(document.getElementById('map'), {
					center: { lat: -33.95, lng: 151.256944 },
					zoom: 11,
					mapTypeId: google.maps.MapTypeId.ROADMAP,
					disableDefaultUI: true,
					// Map controls
					panControl: true,
					zoomControl: true,
					mapTypeControl: true,
					scaleControl: true,
					streetViewControl: true,
					overviewMapControl: true,
					rotateControl: true,
				})

				setMarkers(map)
			}

			function infoWindow(marker) {
				const contentString = '<div id="content" style="display: inline-block;">My Text comes here</div>'

				const infowindow = new google.maps.InfoWindow({
					content: contentString,
					ariaLabel: 'Info Label Here',
					maxWidth: 400,
					// anchor: marker, // Show infowindow on load
				})

				marker.addListener('click', () => {
					infowindow.setPosition(new google.maps.LatLng(marker.position.lat(), marker.position.lng()))
					console.log('Marker click', marker.position.lat(), marker.position.lng(), infowindow.position.lng())
					infowindow.open({
						anchor: marker,
						map,
					})
				})
			}

			// Data for the markers consisting of a name, a LatLng and a zIndex for the
			// order in which these markers should display on top of each other.
			const beaches = [
				// ['Bondi Beach', -33.890542, 151.274856, 4],
				// ['Coogee Beach', -33.923036, 151.259052, 5],
				// ['Cronulla Beach', -34.028249, 151.157507, 3],
				// ['Manly Beach', -33.80010128657071, 151.28747820854187, 2],
				['Maroubra Beach', -33.95, 151.256944, 1],
			]

			function setMarkers(map, cb = null) {
				// Adds markers to the map.
				const image = {
					// url: 'https://developers.google.com/maps/documentation/javascript/examples/full/images/beachflag.png',
					url: 'https://raw.githubusercontent.com/atomjoy/marker/main/google-marker.png',
					// This marker image is 256 pixels wide by 256 pixels high.
					size: new google.maps.Size(256, 256),
					// Scaled size will be 100px x 100px
					scaledSize: new google.maps.Size(40, 40),
					// The origin for this image is (0, 0).
					origin: new google.maps.Point(0, 0),
					// The anchor for this image is the base of the flagpole at (0, 32).
					anchor: new google.maps.Point(20, 20),
				}
				// Shapes define the clickable region of the icon. The type defines an HTML
				// <area> element 'poly' which traces out a polygon as a series of X,Y points.
				// The final coordinate closes the poly by connecting to the first coordinate.
				const shape = {
					coords: [1, 1, 1, 20, 18, 20, 18, 1],
					type: 'poly',
				}

				for (let i = 0; i < beaches.length; i++) {
					const beach = beaches[i]

					// Add marker
					let marker = new google.maps.Marker({
						position: { lat: beach[1], lng: beach[2] },
						map,
						icon: image,
						shape: shape,
						title: beach[0],
						zIndex: beach[3],
					})

					infoWindow(marker)

					// Remove marker example
					// marker.setMap(null);
				}
			}

			window.initMap = initMap
		</script>
		<style>
			#map {
				height: 500px;
			}

			html,
			body {
				height: 100%;
				margin: 0;
				padding: 0;
			}
			.gm-style-iw-t {
				right: 0px !important;
			}
		</style>
	</head>
	<body>
		<div id="map"></div>
	</body>
</html>
```

## Printscreen

<img src="https://raw.githubusercontent.com/atomjoy/marker/main/mapa.png" width="100%">
<img src="https://raw.githubusercontent.com/atomjoy/marker/main/mapa-google.png" width="100%">
