<template>
  <div>
    <h1>Test</h1>
    <router-link :to="{ name: 'Home', params: { num: 5 } }">Home</router-link>
  </div>
</template>

<script>
export default {}
</script>

<style lang="scss" scoped></style>
