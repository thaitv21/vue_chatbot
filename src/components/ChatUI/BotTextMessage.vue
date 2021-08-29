<template>
  <div :style="styles" class="response-text">
    {{ message.text || '' }}
  </div>
</template>

<script>
export default {
  name: "BotTextMessage",
  props: ['message', 'index'],
  computed: {
    styles: function () {
      const localStyle = {
        borderTopLeftRadius: 5,
        borderTopRightRadius: 5,
        borderBottomRightRadius: 5,
        borderBottomLeftRadius: 5,
        marginTop: 0,
        marginBottom: 0
      }
      const index = this.index;
      if (index === 0) {
        localStyle.borderTopLeftRadius = 5
        localStyle.borderTopRightRadius = 20
      }
      if (index === this.messages.length - 1) {
        localStyle.borderBottomRightRadius = 20
        localStyle.borderBottomLeftRadius = 20
      }
      if (index !== 0 && index !== this.messages.length - 1) {
        localStyle.marginTop = 5
      }
      return localStyle;
    }
  }
}
</script>

<style scoped>

</style>
