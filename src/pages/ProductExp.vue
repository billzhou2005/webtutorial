<style lang="scss" scoped>
  .section1 {
    background-image: url('../assets/img/datashow.png');
    background-size: 100% 100%;
    width: 100%;
    height: 960px;
    .notice {
      font: 1.6em sans-serif;
    }
  }
  .section4 {
    background-color: white;
    color: blue;
    background-size: 100% 100%;
    border: medium black;
    width: 100%;
  }
</style>

<template>
  <section class="q-pa-xl flex justify-center section1" >
    <div class="q-pl-xl q-pt-md row notice">{{  }}</div>
  </section>
  <section class="section4 footer">
    <div class="row">
      <div class="q-mt-md col-3 flex flex-center">
        <p>Copyright &copy; 2022</p>
      </div>
      <div class="q-mt-md col-3 flex flex-center">
        <a target="_blank" href="http://www.beian.gov.cn/portal/registerSystemInfo?recordcode=35010202001523" ><img src="../assets/icon-beian.png" style="float:left;"/>
         <p>闽公网安备 35010202001523号</p>
        </a>
      </div>
      <div class="q-mt-md col-3 flex flex-center">
        <p>闽ICP备2022003119号</p>
      </div>
      <div class="col-3 flex flex-center">
        <q-btn to="/" icon-right="home">{{ $t('home') }}</q-btn>
      </div>
    </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'ProductExp'
})
</script>
