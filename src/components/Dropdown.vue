<template>
  <div class="dropdown" ref="dropdownRef">
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
import useClickOutside from "../common/useClickOutside";

import { defineComponent, ref, watch } from "vue";

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
    const dropdownRef = ref<null | HTMLElement>(null);
    const isClickOutSide = useClickOutside(dropdownRef);
    watch(isClickOutSide, () => {
      if (isShowdropDown.value && isClickOutSide.value) {
        isShowdropDown.value = false;
      }
    });
    return {
      isShowdropDown,
      toggleShowDropDown,
      dropdownRef,
    };
  },
});
</script>

<style>
</style>
