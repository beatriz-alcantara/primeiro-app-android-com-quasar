<template>
    <q-page>
        <q-btn label="Scannear QRCode" @click="scanQRCode()"/>
    </q-page>
</template>

<script>
// window.QRScanner.prepare(onDone) // show the prompt

// function onDone (err, status) {
//   if (err) {
//     console.error(err)
//   }
//   if (status.authorized) {
//     window.QRScanner.scan(displayContents)
//     window.QRScanner.show()
//   } else if (status.denied) {
//     alert('acesso negado')
//   }
// }
// function displayContents (err, text) {
//   if (err) {
//   } else {
//     alert(text)
//   }
// }
export default {
  data () {
    return {
      conteudo: null
    }
  },
  mounted () {
    window.QRScanner.prepare(this.onDone)
  },
  destroyed () {
    window.QRScanner.cancelScan(status => {
      console.log('status detroy', status)
    })
  },
  methods: {
    scanQRCode () {
      window.QRScanner.getStatus(status => {
        if (status.authorized) {
          window.QRScanner.scan(this.displayContents)
          window.QRScanner.show()
        }
      })
    },
    onDone (err, status) {
      if (err) {
        console.error(err)
      }
      if (status.authorized) {
        window.QRScanner.scan(this.displayContents)
        window.QRScanner.show()
      } else if (status.denied) {
        alert('acesso negado')
      }
    },
    displayContents (err, text) {
      if (err) {
        alert(err)
      } else {
        alert(text)
      }
    }
  }
}
</script>
