<template>
  <q-layout view="hHh lpR lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
          aria-label="Menu"
        />

        <q-toolbar-title class="absolute-center"
          >Covidu - The coronavirus updates chatbot</q-toolbar-title
        >
      </q-toolbar>
    </q-header>

    <q-drawer
      dark
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      content-class="bg-primary"
    >
      <q-list dark>
        <!--<q-item-label header class="text-white">Menu</q-item-label>-->
        <HomeLink v-for="link in homeLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view />
      </keep-alive>
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink'
import HomeLink from 'components/HomeLink'

export default {
  name: 'MainLayout',

  components: {
    EssentialLink,
    HomeLink
  },

  data() {
    return {
      leftDrawerOpen: false,
      homeLinks: [
        {
          title: 'Home',
          caption: 'Back to home',
          icon: 'home',
          link: '/'
        },
        {
          title: 'Chat',
          caption: 'Chat with Covidu',
          icon: 'chat',
          link: '/chat'
        },
        {
          title: 'About',
          caption: 'About Covidu',
          icon: 'help',
          link: '/about'
        }
      ],
      essentialLinks: [
        {
          title: 'Docs',
          caption: 'quasar.dev',
          icon: 'school',
          link: 'https://quasar.dev'
        },
        {
          title: 'Github',
          caption: 'github.com/quasarframework',
          icon: 'code',
          link: 'https://github.com/quasarframework'
        },
        {
          title: 'Discord Chat Channel',
          caption: 'chat.quasar.dev',
          icon: 'chat',
          link: 'https://chat.quasar.dev'
        },
        {
          title: 'Forum',
          caption: 'forum.quasar.dev',
          icon: 'record_voice_over',
          link: 'https://forum.quasar.dev'
        },
        {
          title: 'Twitter',
          caption: '@quasarframework',
          icon: 'rss_feed',
          link: 'https://twitter.quasar.dev'
        },
        {
          title: 'Facebook',
          caption: '@QuasarFramework',
          icon: 'public',
          link: 'https://facebook.quasar.dev'
        }
      ]
    }
  }
}
</script>
