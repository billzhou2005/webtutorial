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
    height: 440px;
    .title {
      font: 1.8em sans-serif;
    }
    .mycard {
      width: 100%;
      height: 60%;
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
        <div class="row q-pt-md justify-center  mycard">
          <CardIndex
            v-for="card in cards"
            :key="card.index"
            v-bind="card"
          />
        </div>
  </section>
  <section class="section4 footer">
    <div class="row">
      <div class="q-mt-md col-4 flex flex-center">
        <p>Copyright &copy; 2021</p>
      </div>
      <div class="q-mt-md col-4 flex flex-center">
        <p>闽ICP备2022003119号</p>
      </div>
      <div class="col-4 flex flex-center">
        <q-btn to="/" icon-right="home">{{ $t('home') }}</q-btn>
      </div>
    </div>
  </section>
</template>

<script>
import { defineComponent } from 'vue'
import CardIndex from 'components/CardIndex.vue'

export default defineComponent({
  components: { CardIndex },
  name: 'PageIndex',
  data () {
    return {
      cards: [
        { index: 0, points: 'Clojure', suits: 'clojure' },
        { index: 1, points: 'Go', suits: 'go' },
        { index: 2, points: 'Scala', suits: 'scala' },
        { index: 3, points: 'Python', suits: 'python' },
        { index: 4, points: 'AI', suits: 'aisample' },
        { index: 5, points: 'BigData', suits: 'bigdata' }
      ]
    }
  }
})
</script>
