<template>
    <q-page>
        <q-btn label="Scannear QRCode" @click="scanQrcode()"/>
    </q-page>
</template>

<script>
export default {
  data () {
    return {
      conteudo: null
    }
  },
  methods: {
    scanQrcode () {
      // window.QRScanner.prepare((erro, status) => {
      //   console.log('status', status)
      //   console.log('erro', erro)
      // })
      window.QRScanner.getStatus(function (status) {
        console.log('status', status)
      })
    }
  }
}
</script>
