<template>
  <div class="response">
    <div class="user-caption-response-wrapper">
      <div class="caption">
        <div class="caption-text">You</div>
      </div>
    </div>
    <div class="user-response-wrapper">
      <div class="response-text" v-for="(msg, index) in messages" :key="index">
        {{msg.text}}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MessageFromMe",
  props: {
    messages: Array
  }
}
</script>
