<style lang="scss" scoped>
  .section1 {
    background-image: url('../assets/img/productexp.jpg');
    background-size: 100% 100%;
    width: 100%;
    height: 960px;
    .title {
      font: 2.2em sans-serif;
    }
    .download-item {
      font: 1.2em sans-serif;
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
    <div class="items-start">
      <div class="row q-mt-md flex flex-center title">
        <p>"5 10 K"产品体验</p>
      </div>
      <div class="row">
        <div class="q-mt-md col-6 flex flex-left download-item">
          PC版本
        </div>
        <div class="q-mt-md col-6 flex flex-center">
          <button v-on:click="download()">下载</button>
        </div>
      </div>
      <div class="row">
        <div class="q-mt-md col-6 flex flex-left download-item">
          Android版本
        </div>
        <div class="q-mt-md col-6 flex flex-center">
          <button v-on:click="download()">下载</button>
        </div>
      </div>
    </div>
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
import { api } from 'src/boot/axios'

export default defineComponent({
  name: 'ProductExp',
  setup () {
    return {
      download () {
        api({
          url: 'http://192.168.61.3:9092/local/ftkapk',
          method: 'GET',
          responseType: 'blob'
        })
          .then((response) => {
            const url = window.URL
              .createObjectURL(new Blob([response.data]))
            const link = document.createElement('a')
            link.href = url
            link.setAttribute('download', 'ftk.apk')
            document.body.appendChild(link)
            link.click()
          })
      }
    }
  }
})
</script>
