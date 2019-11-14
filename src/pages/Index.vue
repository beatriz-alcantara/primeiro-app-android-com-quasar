<template>
  <q-page class="flex flex-center">
    <div>
      <p>Latidude: {{ localizacao.coords.latitude }}</p>
      <p> Longitude: {{ localizacao.coords.longitude }} </p>
      <q-btn label="Pegar localização" @click="getLocalizacao()"/>
    </div>
  </q-page>
</template>

<script>
document.addEventListener('deviceready', () => {
  console.log('Geolocation pronta')
}, false)
export default {
  name: 'PageIndex',
  data () {
    return {
      localizacao: {
        coords: {
          latitude: null,
          longitude: null
        }
      }
    }
  },
  methods: {
    getLocalizacao () {
      navigator.geolocation.getCurrentPosition((posicao) => {
        console.log('posição: ', posicao)
        this.localizacao = posicao
      })
    }
  },
  created () {
    this.getLocalizacao()
  }
}
</script>
