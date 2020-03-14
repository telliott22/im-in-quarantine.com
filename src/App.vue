<template>
  <div
    id="app"
    class="page"
  >
    <Map />
  </div>
</template>

<script>
import Map from "@/components/Map";

export default {
  name: "App",
  components: {
    Map
  },
  mounted() {
    console.log("app init");
  }
};
</script>
