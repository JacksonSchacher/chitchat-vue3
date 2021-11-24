<template>
  <ChatThread />
  <PostMessage />
</template>

<script>
import ChatThread from './components/ChatThread.vue'
import PostMessage from './components/PostMessage.vue'

export default {
  name: 'App',
  components: {
    ChatThread,
    PostMessage
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
  margin-top: 60px;
}
</style>
