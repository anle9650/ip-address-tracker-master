<template>
  <div>
    <mapbox-map
      :accessToken="accessToken"
      width="100%"
      :center="[lng, lat]"
      :zoom="17"
      @loaded="mapLoaded = true"
    >
      <mapbox-marker
        v-show="mapLoaded"
        :lngLat="[lng, lat]"
        color="black"
        :scale="2"
      />
    </mapbox-map>
  </div>
</template>

<script>
export default {
  name: "LocationMap",
  props: {
    lng: {
      type: Number,
      default: -95,
    },
    lat: {
      type: Number,
      default: 37,
    },
  },
  data() {
    return {
      accessToken:
        "pk.eyJ1IjoiYW5sZTk2NTAiLCJhIjoiY2t6YTc1OWU3MjE5YjJ1bnh2eXo3dXZmbSJ9.OVRTmHR3hpVZJjAk5ymRSg",
      mapLoaded: false,
    };
  },
};
</script>