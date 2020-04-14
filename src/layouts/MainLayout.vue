<template>
  <q-layout view="lHh lpR lFr">
    <q-header class="bg-primary text-white collapse">
      <q-toolbar>
        <q-btn
          dense
          flat
          round
          icon="menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

        <q-toolbar-title>
          <!--<div class="absolute-center">-->
          <q-avatar>
            <img src="statics\app-logo-128x128.png" />
          </q-avatar>
          Covidu
          <!-- </div>-->
        </q-toolbar-title>

        <q-btn dense flat round icon="info" @click="right = !right" />
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above>
      <q-toolbar class="bg-primary text-white collapse">
        <!-- <q-btn
          dense
          flat
          round
          icon="menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />-->
      </q-toolbar>
      <div></div>
      <!--
      <q-list>
        <HomeLink v-for="link in homeLinks" :key="link.title" v-bind="link" />
      </q-list>-->
    </q-drawer>

    <q-drawer show-if-above v-model="right" side="right">
      <!-- drawer content -->
    </q-drawer>

    <q-page-container>
      <keep-alive 
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
<style lang="stylus">

.q-page{
 border-left: 1px solid rgba(0, 0, 0, 0.12);
 border-right: 1px solid rgba(0, 0, 0, 0.12);
}
</style>
