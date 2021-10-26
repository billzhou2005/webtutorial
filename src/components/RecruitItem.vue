<style lang="scss" scoped>
.item {
  font: 1.8em sans-serif;
}
</style>

<template>
    <div class="q-pt-sm q-pl-xl item">
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
  name: 'RecruitItem',
  props: {
    index: {
      type: Number,
      required: true
    },
    catalog: {
      type: String,
      default: 'A'
    },
    description: {
      type: String,
      default: 'recruit1'
    }
  }
})
</script>
