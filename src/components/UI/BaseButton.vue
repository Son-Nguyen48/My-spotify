<template>
  <button
    @click="setID(index) ,showDropDown()"
    :class="`flex items-center justify-start `"
  >
    <slot></slot>
  </button>
</template>

<script>
export default {
  props: ["index"],
  methods: {
    setID(index) {
      this.$emit("set-id", index);
    },
    showDropDown() {
      this.$emit("show-drop-down");
    }
  }
};
</script>

<style></style>
