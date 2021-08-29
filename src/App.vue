<template>
  <div id="app">
    <ChatUI />
  </div>
</template>

<script>
import ChatUI from "@/components/ChatUI/ChatUI";

export default {
  name: 'App',
  components: {
    ChatUI,
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100vh;
}
</style>
