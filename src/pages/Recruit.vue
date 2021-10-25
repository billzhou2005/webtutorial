<style lang="scss" scoped>
  .section1 {
    background-image: url('../assets/img/recruit.jpg');
    background-size: 100% 100%;
    width: 100%;
    height: 960px;
    .notice {
      font: 1.4em sans-serif;
      color: blue;
    }
  }
  .section4 {
    background-color: black;
    color: #ffffff;
    background-size: 100% 100%;
    border: medium black;
    width: 100%;
  }
</style>

<template>
  <section class="q-pt-xl section1" >
    <RecruitItem
      v-for="item in items"
      :key="item.index"
      v-bind="item"
    />
    <div class="q-pl-xl q-pt-md row notice">{{ $t('emailNotice')}}</div>
  </section>
  <section class="section4 footer">
    <div class="row">
      <div class="q-mt-md col-4 flex flex-center">
        <p>Copyright &copy; 2021</p>
      </div>
      <div class="q-mt-md col-4 flex flex-center">
        <p>ICP No.Waiting...</p>
      </div>
      <div class="col-4 flex flex-center">
        <q-btn to="/" icon-right="home">{{ $t('home') }}</q-btn>
      </div>
    </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue'
import RecruitItem from 'components/RecruitItem.vue'

export default defineComponent({
  components: { RecruitItem },
  name: 'Recruit',
  data () {
    return {
      items: [
        { index: 0, catalog: 'A', description: 'recruit1' },
        { index: 1, catalog: 'B', description: 'recruit2' },
        { index: 2, catalog: 'C', description: 'recruit3' },
        { index: 3, catalog: 'D', description: 'recruit4' },
        { index: 4, catalog: 'E', description: 'recruit5' }
      ]
    }
  }
})
</script>
