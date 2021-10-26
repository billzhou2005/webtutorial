<style lang="scss" scoped>
  .section1 {
    background-image: url('../assets/img/productexp.jpg');
    background-size: 100% 100%;
    width: 100%;
    height: 960px;
    .notice {
      font: 1.6em sans-serif;
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
  <section class="q-pa-xl flex justify-center section1" >
    <div class="q-pl-xl q-pt-md row notice">{{ $t('productNotice') }}</div>
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

export default defineComponent({
  name: 'ProductExp'
})
</script>
