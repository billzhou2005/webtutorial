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
  <section class="section1" >
    <div class="q-pt-xl myItems">
      <RecruitItem
        v-for="item in items"
        :key="item.index"
        v-bind="item"
      />
    </div>
    <div class="q-pl-xl q-pt-md row notice">{{ $t('emailNotice')}}</div>
  </section>
  <section class="section4 footer">
    <div class="row">
      <div class="q-mt-md col-3 flex flex-center">
        <p>Copyright &copy; 2021</p>
      </div>
      <div class="q-mt-md col-3 flex flex-center">
        <p>闽ICP备2022003119号</p>
      </div>
      <div class="q-mt-md col-3 flex flex-center">
		 		<a target="_blank" href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=35010202001523" style="display:inline-block;text-decoration:none;height:20px;line-height:20px;"><img src="" style="float:left;"/><p style="float:left;height:20px;line-height:20px;margin: 0px 0px 0px 5px; color:#939393;">闽公网安备 35010202001523号</p></a>
      </div>
      <div class="col-3 flex flex-center">
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
