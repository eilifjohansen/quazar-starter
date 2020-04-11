<template>
  <div class="q-pa-md row justify-center">
    <div style="width: 100%">
      <q-chat-message
        name="Covidu"
        :text="['Hi, what country would you like to check<br> the latest coronavirus stats in?']"
        sent
        text-color="white"
        bg-color="primary"
      >
        <template v-slot:avatar>
          <img
            class="q-message-avatar q-message-avatar--sent"
            src="https://scontent.fosl3-1.fna.fbcdn.net/v/t1.0-9/89266455_112961590318562_634611096208015360_n.jpg?_nc_cat=108&_nc_sid=85a577&_nc_ohc=HC3VlJYOkZEAX_dcpJY&_nc_ht=scontent.fosl3-1.fna&oh=6d32603581bb75296f13397538d814ed&oe=5EB72364"
          >
        </template>
      </q-chat-message>

      <q-chat-message name="You" :text="['Norway']" bg-color="amber"></q-chat-message>

      <q-chat-message name="Covidu" sent text-color="white" bg-color="primary">
        <template v-slot:avatar>
          <img
            class="q-message-avatar q-message-avatar--sent"
            src="https://scontent.fosl3-1.fna.fbcdn.net/v/t1.0-9/89266455_112961590318562_634611096208015360_n.jpg?_nc_cat=108&_nc_sid=85a577&_nc_ohc=HC3VlJYOkZEAX_dcpJY&_nc_ht=scontent.fosl3-1.fna&oh=6d32603581bb75296f13397538d814ed&oe=5EB72364"
          >
        </template>
        <q-spinner-dots size="2rem"/>
      </q-chat-message>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PageIndex'
}
</script>
