<template>
  <div class="input-group">
    <input
      type="text"
      v-model="address"
      class="form-control p-3"
      placeholder="Search for any IP address or domain"
      aria-label="IP address"
      aria-describedby="address-search-button-addon"
    />
    <button
      class="btn btn-submit py-3 px-4"
      type="button"
      id="address-search-button-addon"
      @click="fetchResult"
    >
      <img src="../assets/images/icon-arrow.svg" alt="submit" />
    </button>
  </div>
</template>

<script>
export default {
  name: "AddressSearchBar",
  emits: ["result-fetched"],
  data() {
    return {
      address: "",
    };
  },
  methods: {
    async fetchResult() {
      const response = await fetch(
        `https://geo.ipify.org/api/v2/country,city?apiKey=at_1dNIsUBYryz3CCYKFSR7tYr9rGrk2&ipAddress=${this.address}`
      );
      const result = await response.json();
      this.$emit("result-fetched", result);
    },
  },
};
</script>

<style scoped>
input {
  border-radius: 15px;
}
input:hover {
  cursor: pointer;
}
button.btn-submit {
  background-color: black;
  border-radius: 15px;
}
button.btn-submit:hover {
    background-color: hsl(0, 0%, 17%);
}
</style>