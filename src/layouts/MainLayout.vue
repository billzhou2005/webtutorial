<template>
  <q-layout view="hHh lpR fFf">

    <q-header reveal elevated class="bg-primary text-white" height-hint="98">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-img
            :src="require('../assets/company2.svg')"
            style="height: 32px; max-width: 32px"
          />
          {{ $t('title') }}
        </q-toolbar-title>
        <div align="right">
          <q-select
            v-model="locale"
            :options="localeOptions"
            :label="$t('lang')"
            dense
            emit-value
            map-options
            options-dense
            style="min-width: 150px"
          />
        </div>
      </q-toolbar>

      <q-tabs align="left">
        <q-route-tab to="/" :label = "$t('home')" />
        <q-route-tab to="/About" :label= "$t('about')" />
        <q-route-tab to="/Recruit" :label= "$t('recruit')" />
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
    title: 'MP',
    caption: '+86-19802191202',
    icon: 'smartphone',
    link: '/'
  },
  {
    title: 'Mail',
    caption: 'billzhou2005@gmail.com',
    icon: 'contact_mail',
    link: '/'
  }
]

import { defineComponent, ref } from 'vue'
import { useI18n } from 'vue-i18n'

export default defineComponent({
  name: 'MainLayout',
  components: {
    EssentialLink
  },

  setup () {
    const { locale } = useI18n({ useScope: 'global' })
    const leftDrawerOpen = ref(false)

    return {
      locale,
      localeOptions: [
        { value: 'en-US', label: 'English' },
        { value: 'chn', label: '中文' }
      ],
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
})
</script>
