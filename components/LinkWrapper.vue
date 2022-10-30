<template>
  <NuxtLink :to="{ name: toName, params: { pageId: pageId } }">
    <span>{{label}}</span>
  </NuxtLink>
</template>

<script>
export default {
  props: ["toName", "pageId", "label"]
}
</script>