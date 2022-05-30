<template>
    <div class="mapview-panel">
        <div id="mapview"></div>
        <div id="basemapToggle"></div>
        <div id="scaleBar"></div>
        <div id="Zoom"></div>
    </div>
</template>

<script>
import { loadModules } from 'esri-loader';
const options = {
    url: 'https://js.arcgis.com/4.18/init.js',
    css: 'https://js.arcgis.com/4.18/esri/themes/light/main.css',
}

export default {
    name: 'Mapview',
    components: {},
    mounted: function () {
        console.log(this.$store.state._defaultView);
        this._createMapView();
    },
    methods: {
        async _createMapView() {
            const [Map, Mapview, Basemap, TileLayer, BasemapToggle, ScaleBar, Zoom] = await loadModules(
                ['esri/Map', 'esri/views/MapView', 'esri/Basemap', 'esri/layers/TileLayer',
                    'esri/widgets/BasemapToggle', 'esri/widgets/ScaleBar', 'esri/widgets/Zoom'],
                options
            );

            let basemap = new Basemap({
                baseLayers: [
                    new TileLayer({
                        url: "https://map.geoq.cn/arcgis/rest/services/ChinaOnlineStreetPurplishBlue/MapServer",
                        title: "Basemap"
                    })
                ],
                title: "basemap",
                id: "basemap"
            });

            const map = new Map({
                basemap,
            });
            const mapView = new Mapview({
                container: 'mapview',
                map: map,
                zoom: 10,
                center: [104.098202, 30.666209],
            });

            //实例化地图切换控件
            const basemapToggle = new BasemapToggle({
                view: mapView,
                nextBasemap: "hybrid",
                container: 'basemapToggle'
            });

            mapView.ui.add(basemapToggle);

            //实例化比例尺控件
            const scaleBar = new ScaleBar({
                view: mapView,
                unit: 'metric',
                container: 'scaleBar'
            });

            mapView.ui.add(scaleBar);


            //实例化缩放控件

            const zoom = new Zoom({
                view: mapView,
                container: 'Zoom'
            });

            mapView.ui.add(zoom);




            mapView.ui.components = [];

            this.$store.commit('_setDefaultView', mapView);

            console.log(mapView);

        }
    },
}
</script>

<style>
.mapview-panel,
#mapview {
    position: relative;
    width: 100%;
    height: 100%;
}

#basemapToggle {
    position: absolute;
    right: 15px;
    bottom: 15px;
}

#scaleBar {
    position: absolute;
    left: 15px;
    bottom: 15px;
}

#Zoom {
    position: absolute;
    right: 15px;
    bottom: 100px;
}
</style>
