<template>
  <div class="bg-blue-50 p-4 rounded-sm">
    <p v-html="data" class="text-left"></p>
  </div>
</template>

<script>
export default {
  name: 'Item',
  data() {
    return {};
  },
  props: {
    data: {
      type: String,
      defalut: '',
    },
  },
};
</script>
