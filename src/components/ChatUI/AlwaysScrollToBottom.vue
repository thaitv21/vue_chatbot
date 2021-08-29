<template>
  <div ref="elementRef" />
</template>

<script>
export default {
  name: "AlwaysScrollToBottom",
  mounted() {
    this.$refs.elementRef.scrollIntoView();
  }
}
</script>

<style scoped>

</style>
