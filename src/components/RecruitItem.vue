<style lang="scss" scoped>
.recruit-item {
  max-width: 800px;
  font: 1.8em sans-serif;
}
</style>

<template>
    <div class="q-pt-sm q-pl-xl row recruit-item">
      <q-item clickable v-ripple>
        <q-item-section avatar>
          <q-avatar color="positive" text-color="white"> {{ catalog }} </q-avatar>
        </q-item-section>
        <q-item-section>{{ $t(description) }}</q-item-section>
      </q-item>
    </div>
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
    catalog: {
      type: String,
      default: '0'
    },
    description: {
      type: String,
      default: 'spade'
    }
  }
})
</script>
