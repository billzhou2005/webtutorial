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
        <div class="q-mt-md col-4 flex flex-left download-item">
          PC版本
        </div>
        <div class="q-mt-md col-4 flex flex-center">
          <q-btn color="white" text-color="black" v-on:click="downloadPc()" >下载</q-btn>
        </div>
        <div class="q-mt-md col-4 flex flex-center">
          <q-linear-progress :value="progressPc" color="warning" class="q-mt-sm" />
        </div>
      </div>
      <div class="row">
        <div class="q-mt-md col-4 flex flex-left download-item">
          Android版本
        </div>
        <div class="q-mt-md col-4 flex flex-center">
          <q-btn color="white" text-color="black" v-on:click="downloadAndroid()" >下载</q-btn>
        </div>
        <div class="q-mt-md col-4 flex flex-center">
          <q-linear-progress :value="progressAndroid" color="warning" class="q-mt-sm" />
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
import { defineComponent, ref } from 'vue'
import { api } from 'src/boot/axios'

export default defineComponent({
  name: 'ProductExp',
  setup () {
    const progressPc = ref(0.02)
    const progressAndroid = ref(0.02)
    let isPcFileDownloading = false
    let isAndroidFileDownloading = false

    return {
      progressPc,
      progressAndroid,
      isPcFileDownloading,
      isAndroidFileDownloading,
      downloadPc () {
        if (isPcFileDownloading) {
          return
        }
        const filename = 'test.7z'
        let fileUrl = '/download/'
        fileUrl += filename
        progressPc.value = 0.02
        isPcFileDownloading = true
        console.log('download url:', fileUrl)

        api({
          url: fileUrl,
          method: 'GET',
          responseType: 'blob',
          onDownloadProgress: (evt) => {
            progressPc.value = (evt.loaded / evt.total)
            // console.log('download progress:', progressPc.value)
            if (progressPc.value === 1) {
              isPcFileDownloading = false
            }
          }
        })
          .then((response) => {
            const url = window.URL
              .createObjectURL(new Blob([response.data]))
            const link = document.createElement('a')
            link.href = url
            link.setAttribute('download', filename)
            document.body.appendChild(link)
            link.click()
          })
      },
      downloadAndroid () {
        if (isAndroidFileDownloading) {
          return
        }
        const filename = 'FTK-3D.7z'
        let fileUrl = '/download/'
        fileUrl += filename
        progressAndroid.value = 0.02
        isAndroidFileDownloading = true
        console.log('download url:', fileUrl)

        api({
          url: fileUrl,
          method: 'GET',
          responseType: 'blob',
          onDownloadProgress: (evt) => {
            progressAndroid.value = (evt.loaded / evt.total)
            // console.log('download progress:', progressAndroid.value)
            if (progressAndroid.value === 1) {
              isAndroidFileDownloading = false
            }
          }
        })
          .then((response) => {
            const url = window.URL
              .createObjectURL(new Blob([response.data]))
            const link = document.createElement('a')
            link.href = url
            link.setAttribute('download', filename)
            document.body.appendChild(link)
            link.click()
          })
      }
    }
  }
})
</script>
