<template>
  <div class="container">
    <div class="mx-auto lg:w-1/2 px-10">
      <!-- <div v-if="$fetchState.pending === true">Loading...</div> -->
      <!-- <template v-else>
        <h1 class="title">Nuxt</h1>
        <div class="links">
          <a
            href="https://nuxtjs.org/"
            target="_blank"
            rel="noopener noreferrer"
            class="button--green"
          >
            Documentation
          </a>
          <a
            href="https://github.com/nuxt/nuxt.js"
            target="_blank"
            rel="noopener noreferrer"
            class="button--grey"
          >
            GitHub
          </a>
        </div>
      </template> -->
      <ul class="">
        <li v-for="(item, index) in bibleData" :key="index" class="my-2">
          <Item :data="item" />
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  // middleware({ redirect }) {
  //   return redirect("/tabs");
  // }
  // fetchOnServer: false,
  // fetch() {
  //   console.log('fetching');
  //   return new Promise((resolve) =>
  //     setTimeout(() => {
  //       console.log('fetched');
  //       resolve();
  //     }, 5000)
  //   );
  // },
  data() {
    return {
      bibleData: [],
    };
  },
  mounted() {
    fetch('/bibleTestBoxedQA2022.json')
      .then((response) => {
        return response.json();
      })
      .then((items) => {
        console.log('items: ', items);
        let temp = [];
        for (var key in items) {
          // for (var key1 in items[key]) {
          //   console.log('JSON item: ', items[key][key1]);
          // }
          console.log(key, ': ', items[key].length);
          this.bibleData.push(this.getRandomItem(items[key]));
        }
      });
  },
  methods: {
    getRandomItem(arr) {
      // get random index value
      const randomIndex = Math.floor(Math.random() * arr.length);
      // get random item
      const item = arr[randomIndex];

      return item;
    },
  },
};
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
