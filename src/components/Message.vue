<template>
  <div
    class="message"
    v-if="showMessage"
  >

    <div
      class="message__close"
      @click="hideMessage"
    ></div>

    <h1>Are you in Quarantine?</h1>
    <h1>You're not alone.</h1>
    <p>Corona virus suprised medical professionals around the world, currently infecting x countries</p>

    <ul>
      <li>Confirmed cases: </li>
      <li>Survived: </li>
      <li>Deaths: </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Message",
  mounted() {},
  methods: {
    hideMessage() {
      this.showMessage = false;
    }
  },
  data() {
    return {
      showMessage: true
    };
  }
};
</script>
