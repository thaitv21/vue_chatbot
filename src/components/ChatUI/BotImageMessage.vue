<template>
  <div class="response-img" :style="styles" key="index">
    <img
      src="https://cdn.vox-cdn.com/thumbor/zTBzOjycX07hspHfHerM385iAag=/0x0:2040x1360/1200x800/filters:focal(857x517:1183x843)/cdn.vox-cdn.com/uploads/chorus_image/image/69773669/acastro_210104_1777_google_0001.0.jpg"
      alt="">
  </div>
</template>

<script>
export default {
  name: "BotImageMessage",
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
