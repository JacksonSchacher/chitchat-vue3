<template>
  <main>
    <div class="row">
            <ul id="messages">
                <!-- User Messages -->
            </ul>
        </div>
  </main>
</template>

<script>
import { watchEffect } from '@vue/runtime-core';
import {io} from 'socket.io-client';
export default {
  setup() {
    const socket = io()
    watchEffect(() => {
      socket.on('message', (msg) => {
        let newMessage = document.createElement("LI");
        document.getElementById('messages').append(newMessage).text(msg);
      })
    })
    return {
    }
  }
}
</script>

<style>

</style>