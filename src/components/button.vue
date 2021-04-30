<template>
  <div>
    <button
      class="timeBox__timeBtn-getIn focus:outline-none text-sm py-2 rounded-full border border-green-600 hover:text-gray-900 hover:bg-green-50"
    >
      <slot />
    </button>
  </div>
</template>

<script>
export default {
  name: "btnComponent",
};
</script>

<style lang="scss" scoped></style>
