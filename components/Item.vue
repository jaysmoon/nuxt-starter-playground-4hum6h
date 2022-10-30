<template>
  <div
    class="bg-blue-50 p-4 rounded-md text-left cursor-pointer"
    :class="{ 'bg-red-50': showAnswer === true }"
    @click="handleClick"
  >
    <p class="text-left">
      <strong>Q: {{ data.question }}</strong>
    </p>
    <span v-show="showAnswer" class="text-sm">A: {{ data.answer }}</span>
  </div>
</template>

<script>
export default {
  name: 'Item',
  data() {
    return { showAnswer: false };
  },
  props: {
    data: {
      type: Object,
      defalut: function () {
        return {
          question: 'Question',
          answer: 'answer',
        };
      },
    },
  },
  methods: {
    handleClick() {
      this.showAnswer = !this.showAnswer;
    },
  },
};
</script>
