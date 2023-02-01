<template>
  <div class="flex items-center justify-between">
    <button
      class="text-xl text-white font-semibold hover:underline tracking-tight"
    >
      {{ name }}
    </button>
    <button
      class="text-xs text-lightest uppercase hover:underline tracking-wide font-semibold pt-4"
    >
      Show all
    </button>
  </div>
</template>

<script>
export default {
  props: ["name"]
};
</script>

<style></style>
