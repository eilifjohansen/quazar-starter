<template>
  <q-page class="flex column">
    <q-banner class="bg-grey-4 text-center">Covidu is offline.</q-banner>
    <div class="q-pa-md column col justify-end">
      <q-chat-message
        v-for="message in messages"
        :key="message.id"
        :name="message.from"
        :text="[message.text]"
        :sent="message.from == 'Me' ? true : false"
      >
        <template v-slot:avatar v-if="message.from == 'Covidu' ? true : false">
          <img
            class="q-message-avatar q-message-avatar--sent"
            src="https://scontent.fosl3-1.fna.fbcdn.net/v/t1.0-9/89266455_112961590318562_634611096208015360_n.jpg?_nc_cat=108&_nc_sid=85a577&_nc_ohc=HC3VlJYOkZEAX_dcpJY&_nc_ht=scontent.fosl3-1.fna&oh=6d32603581bb75296f13397538d814ed&oe=5EB72364"
          >
        </template>
      </q-chat-message>
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
          id: 1,
          text:
            'Hi, what country would you like to check<br> the latest coronavirus stats in?',
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

      const payload = {
        location: this.newMessage,
        webhook: 'https://webhook.site/0878e958-df57-4a07-8f59-b43a4d888609',
        userid: '123'
      }

      /*fetch('https://hook.integromat.com/x8bu17plms1trtjtppdryxo6k02bqy9o')
        .then(resp => resp.text())
        .then(function(data) {
          console.log(data)
        })
        .catch(error => console.log(error))
     */
      fetch('https://hook.integromat.com/dtfbvlarirwglzhfsav0inoshn9kggxs', {
        method: 'POST',
        // mode: 'no-cors',
        headers: {
          'Content-Type': 'application/json'
        },
        body: JSON.stringify(payload)
      })
        .then(response => {
          console.log('Status', response.status)

          response.text().then(res => console.log(res))

          this.messages.push({
            text: response.status,
            from: 'Covidu'
          }) 
        })
        .then(result => {
         
       
        })
    }

    // getResponse() {
    //   setTimeout(() => {
    //     fetch('https://hook.integromat.com/dtfbvlarirwglzhfsav0inoshn9kggxs')
    //       .then(response => {
    //         return response.json()
    //       })
    //       .then(data => {
    //         console.log('resultatet er', data)
    //       })
    //   }, 500)
    // }
  }
}
</script>

<style>
</style>
