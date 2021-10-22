<template>
  <q-layout view="hHh lpR fFf">

    <q-header reveal elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Title
        </q-toolbar-title>
        <div align="right">
          <q-select
            filled
            v-model="model"
            :options="options"
            stack-label
            label="Standard"
            color="secondary"
          >
            <template v-slot:selected-item="scope">
              <q-chip
                dense
                square
                color="white"
                text-color="secondary"
                class="q-ma-none"
              >
                <q-avatar color="secondary" text-color="white" :icon="scope.opt.icon" />
                {{ scope.opt.label }}
              </q-chip>
            </template>
          </q-select>
        </div>
      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/" :label = "$t('home')" />
        <q-route-tab to="/About" :label= "$t('about')" />
        <q-route-tab to="/DGame" :label= "$t('dgame')" />
      </q-tabs>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          {{ $t('contact') }}
        </q-item-label>

        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
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
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      model: ref({
        label: 'Google',
        value: 'goog',
        icon: 'mail'
      }),
      options: [
        {
          label: 'Google',
          value: 'goog',
          icon: 'mail'
        },
        {
          label: 'Facebook',
          value: 'fb',
          icon: 'bluetooth'
        }
      ]
    }
  }
})
</script>
