<template>

  <div
    id='map'
    class="map"
  ></div>

</template>


<script>
import mapboxgl from "mapbox-gl";

export default {
  name: "Map",
  components: {},
  mounted() {
    mapboxgl.accessToken =
      "pk.eyJ1IjoidGVsbGlvdHQyMiIsImEiOiJjazdzNXJvbjMwamkzM25xZGZqbmJmY3ptIn0.XLY-uulQLo78uPJlmWlkGw";

    const map = new mapboxgl.Map({
      container: "map",
      style: "mapbox://styles/mapbox/light-v10",
      center: [-96, 37.8],
      zoom: 3
    });

    // Add zoom and rotation controls to the map.
    map.addControl(new mapboxgl.NavigationControl());

    map.on("load", function() {
      /* Sample feature from the `examples.8fgz4egr` tileset:
{
"type": "Feature",
"properties": {
"ethnicity": "White"
},
"geometry": {
"type": "Point",
"coordinates": [ -122.447303, 37.753574 ]
}
}
*/
      map.addSource("ethnicity", {
        type: "vector",
        url: "mapbox://examples.8fgz4egr"
      });

      map.addLayer({
        id: "population",
        type: "circle",
        source: "ethnicity",
        "source-layer": "sf2010",
        paint: {
          // make circles larger as the user zooms from z12 to z22
          "circle-radius": {
            base: 1.75,
            stops: [
              [12, 2],
              [22, 180]
            ]
          },
          // color circles by ethnicity, using a match expression
          // https://docs.mapbox.com/mapbox-gl-js/style-spec/#expressions-match
          "circle-color": [
            "match",
            ["get", "ethnicity"],
            "White",
            "#fbb03b",
            "Black",
            "#223b53",
            "Hispanic",
            "#e55e5e",
            "Asian",
            "#3bb2d0",
            /* other */ "#ccc"
          ]
        }
      });
    });
    console.log(map);
  }
};
</script>
