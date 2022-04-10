<template>
  <div class="card p-2 border-0">
    <div class="card-body d-lg-flex">
      <div class="col mb-3 mb-lg-0 text-lg-start border-lg-end pe-lg-4">
        <h2 class="card-title">IP Address</h2>
        <p class="card-text">{{ result.ip ?? "" }}</p>
      </div>
      <div class="col mb-3 mb-lg-0 text-lg-start border-lg-end px-lg-4">
        <h2 class="card-title">Location</h2>
        <p class="card-text">
          {{ result.location?.city ?? "" }}, {{ result.location?.region ?? "" }}
          {{ result.location?.postalCode ?? "" }}
        </p>
      </div>
      <div class="col mb-3 mb-lg-0 text-lg-start border-lg-end px-lg-4">
        <h2 class="card-title">Timezone</h2>
        <p class="card-text">UTC {{ result.location?.timezone ?? "" }}</p>
      </div>
      <div class="col text-lg-start ps-lg-4">
        <h2 class="card-title">ISP</h2>
        <p class="card-text">{{ result.isp ?? "" }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "LocationCard",
  props: {
    result: { type: Object, default: () => {} },
  },
};
</script>

<style scoped>
.card {
  border-radius: 15px;
}
.card-title {
  text-transform: uppercase;
  color: hsl(0, 0%, 59%);
  font-size: 0.75rem;
  font-weight: 700;
  letter-spacing: 1px;
}
.card-text {
  font-weight: 500;
}

@media screen and (min-width: 992px) {
    .border-lg-end {
        border-right: 1px solid lightgrey;
    }
}
</style>