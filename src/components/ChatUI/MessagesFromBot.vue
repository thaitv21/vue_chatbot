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
      <div v-for="(msg, index) in messages" :key="index">
        <BotImageMessage v-if="msg.image" :message="msg" :index="index"/>
        <BotTextMessage v-else/>
      </div>
    </div>
  </div>
</template>

<script>
import BotTextMessage from "@/components/ChatUI/BotTextMessage";
import BotImageMessage from "@/components/ChatUI/BotImageMessage";
export default {
  name: "MessageFromBot",
  components: {BotImageMessage, BotTextMessage},
  props: {
    messages: Array
  }
}
</script>

<style scoped>

</style>
