<template>
  <q-page class="flex flex-center">
    <div>
      <p>Geolocation: {{ teste }}</p>
      <q-btn label="geolocation" @click="getLocation()"/>
    </div>
  </q-page>
</template>

<script>
// const onDeviceReady = () => {
//   console.log('navigator.geolocation works well')
// }
// document.addEventListener('deviceready', onDeviceReady, false)
export default {
  name: 'PageIndex',
  data () {
    return {
      posicionamento: {
        coords: {
          latitude: null
        }
      },
      teste: null
    }
  },
  methods: {
    getLocation () {
      navigator.geolocation.getCurrentPosition((posicionamento) => {
        // this.posicionamento = posicionamento
        this.teste = 'Olá'
      })
    }
  }
}
</script>
