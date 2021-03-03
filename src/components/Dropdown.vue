<template>
  <div class="dropdown">
    <a
      href="#"
      class="btn btn-outline-light my-2 dropdown-toggle"
      @click.prevent="toggleShowDropDown"
      >{{ title }}</a
    >
    <ul
      class="dropdown-menu"
      :style="{ display: 'block' }"
      v-if="isShowdropDown"
    >
      <slot></slot>
    </ul>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  name: "Dropdown",
  props: {
    title: {
      type: String,
      required: true,
    },
  },
  setup() {
    let isShowdropDown = ref(false);
    function toggleShowDropDown() {
      isShowdropDown.value = !isShowdropDown.value;
    }
    return {
      isShowdropDown,
      toggleShowDropDown,
    };
  },
});
</script>

<style>
</style>
