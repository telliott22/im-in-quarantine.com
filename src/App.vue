<template>
  <div
    id="app"
    class="page"
  >
    <message />
    <Map />
  </div>
</template>

<script>
import Message from "@/components/Message";
import Map from "@/components/Map";

export default {
  name: "App",
  components: {
    Map,
    Message
  },
  mounted() {
    console.log("app init");
  }
};
</script>
  