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
    background-color: black;
    color: #ffffff;
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
        <q-lable class="notice">请留下你的联系方式:</q-lable>
        <q-input
          filled
          bg-color="blue-grey-2"
          v-model="name"
          label="Your name *"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Please type something']"
        />

        <q-input v-model="tel" filled bg-color="blue-grey-2" type="tel" label="Your telephone" hint=" " />
        <q-input v-model="email" filled bg-color="blue-grey-2" type="email" label="Your email *" hint=" " />
        <q-input
          v-model="text"
          filled
          bg-color="blue-grey-2"
          autogrow
          label="Cooperation contents"
          hint=" "
        />

        <div>
          <q-btn label="Submit" type="submit" color="primary"/>
          <q-btn label="Reset" type="reset" color="primary" flat class="q-ml-sm" />
        </div>
      </q-form>

    </div>
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
import { defineComponent, ref } from 'vue'
import { useQuasar } from 'quasar'

export default defineComponent({
  name: 'bizCooperation',
  setup () {
    const $q = useQuasar()
    const name = ref(null)
    const tel = ref(null)
    const email = ref(null)
    const text = ref(null)

    return {
      name,
      tel,
      email,
      text,

      onSubmit () {
        if (tel.value == null) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'You need to fill a phone number'
          })
        } else {
          console.log(name, tel, email, text)
          $q.notify({
            color: 'green-4',
            textColor: 'white',
            icon: 'cloud_done',
            message: 'Submitted'
          })
        }
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
