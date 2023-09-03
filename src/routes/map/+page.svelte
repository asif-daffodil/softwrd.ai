<!-- Map.svelte -->
<script>
    import { onMount } from "svelte";
    import Map from "ol/Map";
    import View from "ol/View";
    import TileLayer from "ol/layer/Tile";
    import OSM from "ol/source/OSM";
    import Navlink from "../../lib/Navlink.svelte";
    import GeoJSON from "ol/format/GeoJSON";
    import VectorLayer from "ol/layer/Vector";
    import VectorSource from "ol/source/Vector";
    import Style from "ol/style/Style";
    import Fill from "ol/style/Fill";

    let map;

    onMount(() => {
        // Initialize the OpenLayers map
        /* map = new Map({
            target: "map",
            layers: [
                new TileLayer({
                    source: new OSM(),
                }),
            ],
            view: new View({
                center: [0, 0],
                zoom: 2,
            }),
        }); */
        // Load the GeoJSON data
        fetch(geojson)
            .then((response) => response.json())
            .then((geojson) => {
                // Create a VectorSource from the GeoJSON data
                const vectorSource = new VectorSource({
                    features: new GeoJSON().readFeatures(geojson),
                });

                // Create a VectorLayer with the desired style
                const vectorLayer = new VectorLayer({
                    source: vectorSource,
                    style: new Style({
                        fill: new Fill({
                            color: "rgba(0, 106, 78, 0.75)", // #006a4e with 0.75 opacity
                        }),
                    }),
                });

                // Add the VectorLayer to the map
                map.addLayer(vectorLayer);
            });
    });
</script>

<Navlink />

<div id="map" />

<style>
    #map {
        width: 100%;
        height: calc(100vh - 4rem);
    }
</style>
