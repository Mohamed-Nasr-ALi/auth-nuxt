<template>
  <div class="container mx-auto">
    <TheHeader/>
    <Nuxt />
  </div>
</template>

<script>
import TheHeader from "../components/TheHeader";
export default {
  name: "default",
  components: {TheHeader}
}
</script>

<style scoped>

</style>
