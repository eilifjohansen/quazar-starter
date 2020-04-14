<template>
  <q-layout view="hHh lpR lFr">
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn
          dense
          flat
          round
          icon="menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          <div class="absolute-center">
            <q-avatar>
              <img src="statics\app-logo-128x128.png" />
            </q-avatar>
            Covidu
          </div>
        </q-toolbar-title>

        <q-btn dense flat round icon="info" @click="right = !right" />
      </q-toolbar>
    </q-header>

    <!-- <q-header elevated>
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="left = !left" />

        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
          aria-label="Menu"
        />

        <q-toolbar-title class="absolute-center">Covidu</q-toolbar-title>

        <q-btn dense flat round icon="menu" @click="right = !right" />
      </q-toolbar>
    </q-header>-->

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered>
      <!--
      <q-list>
        <HomeLink v-for="link in homeLinks" :key="link.title" v-bind="link" />
      </q-list>-->
    </q-drawer>

    <q-drawer show-if-above v-model="right" side="right" bordered>
      <!-- drawer content -->
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
      right: false,
      leftDrawerOpen: false,
      homeLinks: [
        {
          title: 'Chat with Covidu',
          caption: 'Chat with Covidu',
          icon: 'chat',
          link: '/'
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
