<template>
  <div class="chat-app-wrapper">
    <div v-if="open" class="chat-open">
      <div class="chat-app">
        <div class="top">
          <div class="avatar">
            <img src="@/assets/logo.png" alt=""/>
          </div>
          <div class="company">
            <div class="header">ChatBot</div>
            <div class="status">online</div>
          </div>
        </div>
        <div class="conversation">
          <div v-for="(item, index) in messages" :key="index">
            <MessageFromMe v-if="item.from === 'me'" :messages="item.messages"/>
            <MessageFromBot v-else :messages="item.messages"/>
            <BotLoading v-if="loading"/>
            <AlwaysScrollToBottom/>
          </div>
        </div>
        <div class="typing">
          <input
              type="text" :maxlength="256" placeholder="Type your message here" v-model="typingMessage"
              :disabled="loading" @keyup.enter="sendMessage"/>
          <div class="send-icon" @click="sendMessage">
            <img src="@/assets/logo.png" alt='' />
          </div>
        </div>
        <div class="power-by">Powered by VIETTEL</div>
      </div>
    </div>
    <div v-else @click="open = true" class="chat-close">
      <div class="bubble">
        <img src="@/assets/logo.png" alt="" />
      </div>
    </div>
  </div>
</template>

<script>
import MessageFromMe from "@/components/ChatUI/MessagesFromMe";
import MessageFromBot from "@/components/ChatUI/MessagesFromBot";
import BotLoading from "@/components/ChatUI/BotLoading";
import AlwaysScrollToBottom from "@/components/ChatUI/AlwaysScrollToBottom";
import '@/assets/chatui.css';

const sendMessageToServer = async (message) => {
  // eslint-disable-next-line no-undef
  const response = await fetch(
      'http://18.139.217.55:5005/webhooks/rest/webhook',
      {
        method: 'POST',
        body: JSON.stringify({
          sender: 'test_user',
          message: message,
          metadata: {}
        })
      }
  )
  const data = await response.json()
  return data.map((item) => {
    if (item.image) {
      return { image: item.image }
    } else {
      return { text: item.text }
    }
  });
}

export default {
  name: "ChatUI",
  components: {AlwaysScrollToBottom, BotLoading, MessageFromBot, MessageFromMe},
  data: function () {
    return {
      messages: [],
      typingMessage: '',
      loading: false,
      open: false,
    }
  },
  methods: {
    sendMessage: function () {
      console.log('enter', this.typingMessage);
      const typingMessage = this.typingMessage.trim();
      if (!typingMessage) {
        return
      }
      this.typingMessage = '';
      this.messages.push({from: 'me', messages: [{ text: typingMessage }]});
      sendMessageToServer(typingMessage).then((botMessages) => {
        this.messages.push({from: 'bot', messages: botMessages});
        this.loading = false;
      });
    },
  }
}
</script>

<style scoped>

</style>
