<template>
  <div id="app">
    <div class="container flex justify-center">
      <user-time-tracker />
    </div>
  </div>
</template>

<script>
import UserTimeTracker from "./components/userTimeTracker.vue";
export default {
  components: { UserTimeTracker },
};
</script>

<style>
#app {
  width: 100%;
  display: flex;
  justify-content: center;
}
</style>
