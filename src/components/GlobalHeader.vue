<template>
  <nav class="navbar navbar-dark bg-primary justify-content-between mb-4 px-4">
    <a href="#" class="navbar-brand">lastcode专栏</a>
    <ul v-if="!user.isLogin" class="list-inline mb-0">
      <li class="list-inline-item">
        <a href="#" class="btn btn-outline-light my-2">登录</a>
      </li>
      <li class="list-inline-item">
        <a href="#" class="btn btn-outline-light my-2">注册</a>
      </li>
    </ul>
    <ul v-else>
      <li class="list-inline-item">
        <dropdown :title="`你好 ${user.name}`">
          <dropdow-item>
            <a href="#" class="dropdown-item">新建文章</a></dropdow-item
          >
          <dropdow-item disabled>
            <a href="#" class="dropdown-item">编辑资料</a></dropdow-item
          >
          <dropdow-item>
            <a href="#" class="dropdown-item">退出登录</a></dropdow-item
          >
        </dropdown>
      </li>
    </ul>
  </nav>
</template>

<script lang="ts">
import Dropdown from "./Dropdown.vue";
import DropdownItem from "./DropdownItem.vue";

import { defineComponent, PropType } from "vue";

export interface UserProps {
  isLogin: boolean;
  name?: string;
  id?: number;
}
export default defineComponent({
  props: {
    user: {
      type: Object as PropType<UserProps>,
      required: true,
    },
  },
  components: {
    Dropdown,
  },
});
</script>

<style>
</style>