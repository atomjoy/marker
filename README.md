# Map marker images
Google map marker images.

## Url

```sh
https://raw.githubusercontent.com/atomjoy/marker/main/google-marker.png
https://raw.githubusercontent.com/atomjoy/marker/main/google-marker-big.png
https://raw.githubusercontent.com/atomjoy/marker/main/google-marker-3d.png
```

## Sample map

<https://developers.google.com/maps/documentation/javascript/examples/marker-simple>

```html
<html>
	<head>
		<title>Simple Map</title>

		<!-- Old google map -->
		<script src="https://maps.googleapis.com/maps/api/js?key=AIzaSyB41DRUbKWJHPxaFjMAwdrzWzbVKartNGg&callback=initMap&v=weekly" defer></script>

		<!--
      <link rel="stylesheet" type="text/css" href="./style.css" />
  		<script type="module" src="./index.js"></script>
    -->

		<script>			
			function initMap() {
				const map = new google.maps.Map(document.getElementById('map'), {
					center: { lat: -33.9, lng: 151.2 },
					zoom: 11,
				})

				setMarkers(map)
			}

			// Data for the markers consisting of a name, a LatLng and a zIndex for the
			// order in which these markers should display on top of each other.
			const beaches = [
				// ['Bondi Beach', -33.890542, 151.274856, 4],
				// ['Coogee Beach', -33.923036, 151.259052, 5],
				// ['Cronulla Beach', -34.028249, 151.157507, 3],
				// ['Manly Beach', -33.80010128657071, 151.28747820854187, 2],
				['Maroubra Beach', -33.950198, 151.259302, 1],
			]

			function setMarkers(map) {
				// Adds markers to the map.
				const image = {
					// url: 'https://developers.google.com/maps/documentation/javascript/examples/full/images/beachflag.png',
					url: 'https://raw.githubusercontent.com/atomjoy/marker/main/google-marker.png',
					// This marker is 20 pixels wide by 32 pixels high.
					size: new google.maps.Size(20, 32),
					// The origin for this image is (0, 0).
					origin: new google.maps.Point(0, 0),
					// The anchor for this image is the base of the flagpole at (0, 32).
					anchor: new google.maps.Point(0, 32),
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

					new google.maps.Marker({
						position: { lat: beach[1], lng: beach[2] },
						map,
						icon: image,
						shape: shape,
						title: beach[0],
						zIndex: beach[3],
					})
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
		</style>
	</head>
	<body>
		<div id="map"></div>		
	</body>
</html>
```
