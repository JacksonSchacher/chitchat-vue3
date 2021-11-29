<template>
<main>
        <div class="row">
            <div class="col-lg-6">
                <form @submit.prevent="postMessage()">
                    <div class="input-group">
                        <input type="text" name="message" id="message" class="form-control" placeholder="Message.." aria-label="Message.." v-model="editable.message" required>
                        <span class="input-group-btn">
                    <button class="btn btn-secondary" type="submit">Send</button>
                  </span>
                    </div>
                </form>
            </div>
        </div>
</main>
</template>

<script>
import { ref } from '@vue/reactivity';
import { io } from 'socket.io-client';
import { socketService } from '../socketService.js'

export default {
  setup() {
    const editable = ref({})
    const socket = io();
    return {
      editable,
      async postMessage() {
        try {
          let msg = editable.value;
          console.log(editable.value)
          await socketService.postMessage(msg)
          // socket.emit('message', {msg}); Probably should be handled by the service
          editable.value = {};
        } catch (error) {
          console.log(error);
        }
      }
    }
  }
}
</script>

<style>

</style>