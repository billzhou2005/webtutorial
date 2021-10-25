<style lang="sass" scoped>
.my-card
  width: 15%
  height: 310px
  color: #000000
  background-color: #FFFFFF
</style>

<template>
  <q-card dark bordered class="q-ml-md shadow-3 my-card">
    <q-card-section>
      <q-img
        :src="require('../assets/img/'+suits+'.png')"
      />
    </q-card-section>
    <q-card-section class="flex flex-center">
      <div class="text-h6">{{points}}</div>
    </q-card-section>
  </q-card>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'CardFront',
  props: {
    index: {
      type: Number,
      required: true
    },
    points: {
      type: String,
      default: '0'
    },
    suits: {
      type: String,
      default: 'spade'
    }
  }
})
</script>
