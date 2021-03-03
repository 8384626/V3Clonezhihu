<template>
  <div class="container">
    <global-header :user="currentUser"></global-header>
    <column-list :list="list"></column-list>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import "bootstrap/dist/css/bootstrap.min.css";
import ColumnList, { ColumnProps } from "./components/ColumnList.vue";
import GlobalHeader, { UserProps } from './components/GlobalHeader.vue'
const currentUser:UserProps = {
  isLogin:true,
  name:'lastcode'
}
const testData: ColumnProps[] = [
  {
    id: 1,
    title: "lastcode的专栏",
    description: "这是test1专栏,有一段非常有趣的言论这是test1专栏,有一段非常有趣的言论这是test1专栏,有一段非常有趣的言论",
    avatar: "https://i03piccdn.sogoucdn.com/b0e20da1fef526f0",
  },
  {
    id: 2,
    title: "lastcode2的专栏",
    description: "这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论",
    avatar: "https://i03piccdn.sogoucdn.com/b0e20da1fef526f0",
  },
  {
    id: 3,
    title: "lastcode3的专栏",
    description: "这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论",
  },
  {
    id: 4,
    title: "lastcode4的专栏",
    description: "这是test4专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论这是test2专栏,有一段非常有趣的言论",
    avatar: "https://i03piccdn.sogoucdn.com/b0e20da1fef526f0",
  },
];

export default defineComponent({
  name: "App",
  setup() {
    return {
      list: testData,
      currentUser
    };
  },
  components: {
    ColumnList,
    GlobalHeader
  },
});
</script>

<style>
</style>
