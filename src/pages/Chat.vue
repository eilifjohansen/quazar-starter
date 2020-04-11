<template>
  <q-page class="flex column">
    <q-banner class="bg-grey-4 text-center">Covidu is offline.</q-banner>
    <div class="q-pa-md column col justify-end">
      <q-chat-message
        v-for="message in messages"
        :key="message.text"
        :name="message.from"
        :text="[message.text]"
        :sent="message.from == 'Me' ? true : false"
      />
    </div>
    <q-footer elevated>
      <q-toolbar>
        <q-form @submit="sendMessage" class="full-width">
          <q-input v-model="newMessage" bg-color="white" outlined rounded label="Message" dense>
            <template v-slot:after>
              <q-btn @click="sendMessage" round dense flat color="white" icon="send"/>
            </template>
          </q-input>
        </q-form>
      </q-toolbar>
    </q-footer>
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      newMessage: '',
      messages: [
        {
          text:
            'Hi, what country would you like to check<br> the latest coronavirus stats in?',
          from: 'Covidu'
        },
        {
          text: 'Norway',
          from: 'Me'
        },
        {
          text: 'Just a moment...',
          from: 'Covidu'
        }
      ]
    }
  },
  methods: {
    sendMessage() {
      this.messages.push({
        text: this.newMessage,
        from: 'Me'
      })
    }
  }
}
</script>

<style>
</style>
