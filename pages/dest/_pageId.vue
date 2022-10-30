<template>
  <div class="container">
    <h1>This is page {{pageId}}</h1>
    <NuxtLink to="/tabs">Back to tabs</NuxtLink>
  </div>
  
</template>

<script>
export default {
  async asyncData({ params }) {
    return params;
  }
}
</script>

<style>
</style>