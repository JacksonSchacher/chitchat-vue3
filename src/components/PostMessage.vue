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
export default {
  setup() {
    const editable = ref({})
    const socket = io();
    return {
      editable,
      postMessage() {
        try {
          let msg = editable.value;
          console.log(editable.value)
          socket.emit('message', {msg});
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