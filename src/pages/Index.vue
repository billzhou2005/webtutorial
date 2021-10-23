<style lang="scss" scoped>
  .section1 {
    background-image: url('../assets/surreal-dream.jpg');
    background-size: 100% 100%;
    width: 100%;
    height: 600px;
    .dream1 {
      font: 4em sans-serif;
    }
    .dream2 {
      font: 2.2em sans-serif;
    }
  }
  .section2 {
    background-color: #c4dfd0;
    background-size: 100% 100%;
    border: medium black;
    margin: 2px;
    width: 100%;
    height: 440px;
    .title {
      font: 1.8em sans-serif;
    }
  }
  .section3 {
    background-color: #c4dfd0;
    background-size: 100% 100%;
    border: medium black;
    width: 100%;
    height: 360px;
    .title {
      font: 1.8em sans-serif;
    }
    .my-card {
      width: 15%;
      height: 100%;
    }
  }
  .bak {
    background-color: #145a32;
    background-size: 100% 100%;
    border: medium dashed black;
    margin: 2px;
    border-radius: 10%;
    width: 800px;
    height: 440px;
  }
</style>

<template>
  <section class="section1" >
    <div class="q-pt-xl flex flex-center row dream1">Light up your dreams!</div>
    <div class="q-pt-md flex flex-center row dream2">点燃您的梦想</div>
  </section>
  <section class="section2" >
    <div class="container">
        <p class="q-pt-md text-center title"> {{ $t('welcome')}} </p>
        <div class="q-pt-xl row text-center">
            <div class="col-4">
                <q-icon name="description" class="text-primary" style="font-size: 4.4em;" />
                <h3>10,869,609</h3>
                <p class="text-dark" style="font-size: 1.2em;">{{ $t('deployments')}}</p>
            </div>
            <div class="col-4">
                <q-icon name="inventory" class="text-secondary" style="font-size: 4.4em;" />
                <h3>987 TB</h3>
                <p class="text-dark" style="font-size: 1.2em;">{{ $t('contents')}}</p>
            </div>
            <div class="col-4">
                <q-icon name="engineering" class="text-accent" style="font-size: 4.4em;" />
                <h3>1,608+</h3>
                <p class="text-dark" style="font-size: 1.2em;">{{ $t('projects')}}</p>
            </div>
        </div>
    </div>
  </section>
  <section class="section3">
        <p class="q-pt-md text-center title"> {{ $t('technical')}} </p>
        <div class="row flex flex-center">
          <q-card class="q-mr-xs my-card">
            <img :src="require('../assets/company2.svg')" style="height: 120px; max-width: 180px">
            <q-card-section>
              <div class="text-h6">Our Changing Planet</div>
              <div class="text-subtitle2">by John Doe</div>
            </q-card-section>
          </q-card>
          <q-card class="q-mr-xs my-card">
            <img src="https://cdn.quasar.dev/img/mountains.jpg">
            <q-card-section>
              <div class="text-h6">Our Changing Planet</div>
              <div class="text-subtitle2">by John Doe</div>
            </q-card-section>
          </q-card>
          <q-card class="q-mr-xs my-card">
            <img src="https://cdn.quasar.dev/img/mountains.jpg">
            <q-card-section>
              <div class="text-h6">Our Changing Planet</div>
              <div class="text-subtitle2">by John Doe</div>
            </q-card-section>
          </q-card>
          <q-card class="q-mr-xs my-card">
            <img src="https://cdn.quasar.dev/img/mountains.jpg">
            <q-card-section>
              <div class="text-h6">Our Changing Planet</div>
              <div class="text-subtitle2">by John Doe</div>
            </q-card-section>
          </q-card>
          <q-card class="q-mr-xs my-card">
            <img src="https://cdn.quasar.dev/img/mountains.jpg">
            <q-card-section>
              <div class="text-h6">Our Changing Planet</div>
              <div class="text-subtitle2">by John Doe</div>
            </q-card-section>
          </q-card>
          <q-card class="q-mr-xs my-card">
            <img src="https://cdn.quasar.dev/img/mountains.jpg">
            <q-card-section>
              <div class="text-h6">Our Changing Planet</div>
              <div class="text-subtitle2">by John Doe</div>
            </q-card-section>
          </q-card>
        </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'PageIndex'
})
</script>
