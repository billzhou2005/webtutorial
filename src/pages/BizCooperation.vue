<style lang="scss" scoped>
  .section1 {
    background-image: url('../assets/img/cooperation.jpg');
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
    <div class="q-pa-md" style="max-width: 400px">
      <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-sm"
      >
        <q-lable class="notice">{{ $t('bizContactNotice') }}</q-lable>
        <q-input
          filled
          bg-color="blue-grey-2"
          v-model="name"
          :label="$t('bizName')"
          lazy-rules
          :rules="[ val => val && val.length > 0 || $t('bizNameNotice') ]"
        />

        <q-input
          v-model="tel"
          filled bg-color="blue-grey-2"
          type="tel"
          :label="$t('bizTel')"
          hint=" "
          lazy-rules
          :rules="[ val => val && val.length > 10 || $t('bizTelNotice') ]"
        />
        <q-input v-model="email" filled bg-color="blue-grey-2" type="email" :label="$t('bizEmail')" hint=" " />
        <q-input
          v-model="text"
          filled
          bg-color="blue-grey-2"
          autogrow
          :label="$t('bizComment')"
          hint=" "
        />

        <div>
          <q-btn :label="$t('submit')" type="submit" color="primary"/>
          <q-btn :label="$t('reset')" type="reset" color="primary" flat class="q-ml-sm" />
        </div>
      </q-form>

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
import { useQuasar } from 'quasar'
import { useI18n } from 'vue-i18n'
import { api } from 'src/boot/axios'

export default defineComponent({
  name: 'bizCooperation',
  setup () {
    const $q = useQuasar()
    const { t, locale } = useI18n({ useScope: 'global' })
    const name = ref(null)
    const tel = ref(null)
    const email = ref(null)
    const text = ref(null)
    const form = {
      name: '',
      tel: '',
      email: '',
      description: '',
      locale: ''
    }

    return {
      name,
      tel,
      email,
      text,

      onSubmit () {
        form.name = name.value
        form.tel = tel.value
        form.email = email.value
        form.description = text.value
        form.locale = locale.value

        console.log(form)
        api.post('/bizinfo', form).then((res) => {
          console.log(res.data)
        }).catch((err) => {
          console.log(err)
        })

        $q.notify({ color: 'green-4', textColor: 'white', icon: 'cloud_done', message: t('submitNotice') })
      },

      onReset () {
        name.value = null
        tel.value = null
        email.value = null
        text.value = null
      }
    }
  }
})
</script>
