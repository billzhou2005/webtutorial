<style lang="scss" scoped>
  .section1 {
    background-image: url('../assets/img/cooperation.jpg');
    background-size: 100% 100%;
    width: 100%;
    height: 960px;
    .email-notice {
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
  <section class="q-pa-xl flex justify-center section1" >
    <div class="q-pa-md" style="max-width: 400px">

      <q-form
        @submit="onSubmit"
        @reset="onReset"
        class="q-gutter-md"
      >
        <q-input
          filled
          v-model="name"
          label="Your name *"
          hint="Name and surname"
          lazy-rules
          :rules="[ val => val && val.length > 0 || 'Please type something']"
        />

        <q-input
          filled
          type="number"
          v-model="age"
          label="Your age *"
          lazy-rules
          :rules="[
            val => val !== null && val !== '' || 'Please type your age',
            val => val > 0 && val < 100 || 'Please type a real age'
          ]"
        />
        <q-input v-model="tel" filled type="tel" hint="Telephone number" />
        <q-input v-model="email" filled type="email" hint="Email" />
        <q-input
          v-model="text"
          filled
          autogrow
          hint="Cooperation description"
        />

        <q-toggle v-model="accept" label="I accept the license and terms" />
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
    const age = ref(null)
    const accept = ref(false)

    return {
      name,
      age,
      accept,
      email: ref(''),
      tel: ref(''),
      text: ref(''),

      onSubmit () {
        if (accept.value !== true) {
          $q.notify({
            color: 'red-5',
            textColor: 'white',
            icon: 'warning',
            message: 'You need to accept the license and terms first'
          })
        } else {
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
        age.value = null
        accept.value = false
      }
    }
  }
})
</script>
