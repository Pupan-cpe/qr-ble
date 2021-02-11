<template>
  <div>
    <div>
      <a
        href="https://chat-api.one.th/go_api/api/v1/openScanQRcodeWithValue"
        target="_blank"
        >--------Scan QR--------</a
      >
    </div>
    <h1> <button
          @click="scanDevice()" color="pink">scandevice
        </button></h1>
    {{pupan}}
  </div>
</template>

<script>
export default {
  data () {
    return {
      pupan: ''

    }
  },
  created () {

  },
  mounted () {
    window.addEventListener('oneChatCallBackQRScanner', async (e) => {
      alert(e.detail.qrcode)
      this.pupan = e.detail.qrcode
    })
    window.addEventListener('oneChatBluetootchCallBackData', async (e) => {
      this.data = e.detail
      alert(this.data)
    })
  },
  methods: {
    scanDevice () {
      alert('scanDevice')
      try {
        window.webkit.messageHandlers.OneChat_scanDevice.postMessage(5000)
        alert('scanDevice2')
      } catch (error) {
        alert('scanDevice ' + error)
      }
    }
  }

}

</script>

<style lang="scss" scoped>
</style>
