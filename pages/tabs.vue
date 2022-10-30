<!-- 
    - download this project to test locally, "call stack exceeded" error is specific to stackblitz
    - rerenders can be checked in performance tab of Vue dev tools 
  -->
<template>   
  <div class="container">
    <div class="tabs container">
      <button v-for="tab in tabs" @click="currentTab = tab">{{tab.label}}</button>
    </div>
    <!-- This will trigger rerender of every NuxtLink on tab swtich -->
    <!-- <div>
      <ul v-show="tab === currentTab" v-for="tab in tabs" :key="tab.label">
        <li v-for="item in tab.children" :key="item.id">
          <NuxtLink :to="{ name: 'dest-pageId', params: { pageId: item.id } }">
            <span>{{item.label}}</span>
          </NuxtLink>
        </li>
      </ul>
    </div> -->
    <!-- This will not trigger rerender of any NuxtLink on tab swtich -->
    <div>
      <ul v-show="tab === currentTab" v-for="tab in tabs" :key="tab.label">
        <li v-for="item in tab.children" :key="item.id">
          <LinkWrapper
            to-name="dest-pageId"
            :page-id="item.id"
            :label="item.label"
          ></LinkWrapper>
        </li>
      </ul>
    </div>   
  </div>
</template>

<script>
import {tabs} from "./tabs-data.js";
import LinkWrapper from "~/components/LinkWrapper";

export default {
  data() {
    return {
      tabs,
      currentTab: tabs[0]
    };
  },
  components: {LinkWrapper}
}
</script>

<style>
.container {
  padding: 20px;
}
</style>
