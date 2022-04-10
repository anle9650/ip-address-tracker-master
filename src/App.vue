<template>
  <header class="p-4">
    <h1 class="text-white mb-4">IP Address Tracker</h1>
    <AddressSearchBar
      class="mb-4 mb-lg-5 mx-auto w-lg-33"
      @result-fetched="(result) => (this.result = result)"
    />
    <LocationCard
      v-if="result"
      :result="result"
      class="shadow on-top mx-auto w-lg-75"
    />
  </header>
  <section>
    <LocationMap
      :lng="result?.location?.lng"
      :lat="result?.location?.lat"
      class="mapbox-map"
    />
  </section>
  <footer class="attribution">
    Challenge by
    <a href="https://www.frontendmentor.io?ref=challenge" target="_blank"
      >Frontend Mentor</a
    >. Coded by <a href="#">Andy Le</a>.
  </footer>
</template>

<script>
import AddressSearchBar from "./components/AddressSearchBar.vue";
import LocationCard from "./components/LocationCard.vue";
import LocationMap from "./components/LocationMap.vue";

export default {
  name: "App",
  components: {
    AddressSearchBar,
    LocationCard,
    LocationMap,
  },
  data() {
    return {
      result: null,
    };
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik:wght@400;500;700&display=swap");

#app {
  font-family: "Rubik", sans-serif;
  font-size: 18px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

header {
  background-image: url("./assets/images/pattern-bg.png");
  height: 45vh;
}

.on-top {
  z-index: 999;
}

.mapbox-map {
  height: 600px;
}

@media screen and (min-width: 992px) {
  header {
    height: 30vh;
  }
  .mapbox-map {
    height: 700px;
  }
  .w-lg-33 {
    width: 33vw;
  }
  .w-lg-75 {
    width: 75vw;
  }
}

.attribution {
  font-size: 11px;
  text-align: center;
}
.attribution a {
  color: hsl(228, 45%, 44%);
}
</style>
