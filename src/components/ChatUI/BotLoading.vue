<template>
  <div class="response">
    <div class="bot-caption-response-wrapper">
      <div class="caption">
        <div class="avatar">
          <img src="@/assets/logo.png" alt='' />
        </div>
        <div class="caption-text">Bot</div>
      </div>
    </div>
    <div class="bot-response-wrapper">
      <div class="bot-loading response-text">
        <div class="wave">
          <span class="dot"/>
          <span class="dot"/>
          <span class="dot"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "BotLoading"
}
</script>

<style scoped>
.bot-loading {
  border-radius: 5px 20px 20px 20px;
}
</style>
