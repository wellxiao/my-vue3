<template>
  <div>
    <router-view></router-view>
    <hello-world msg="Hello Vue 3.0 + Vite" />
  </div>
</template>

<script lang="ts">
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
</script>
