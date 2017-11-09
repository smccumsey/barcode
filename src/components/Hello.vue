<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>Essential Links</h2>
    <ul>
      <li><a href="https://vuejs.org" target="_blank">Core Docs</a></li>
      <li><a href="https://forum.vuejs.org" target="_blank">Forum</a></li>
      <li><a href="https://chat.vuejs.org" target="_blank">Community Chat</a></li>
      <li><a href="https://twitter.com/vuejs" target="_blank">Twitter</a></li>
      <br>
      <li><a href="http://vuejs-templates.github.io/webpack/" target="_blank">Docs for This Template</a></li>
    </ul>
    <h2>Ecosystem</h2>
    <ul>
      <li><a href="http://router.vuejs.org/" target="_blank">vue-router</a></li>
      <li><a href="http://vuex.vuejs.org/" target="_blank">vuex</a></li>
      <li><a href="http://vue-loader.vuejs.org/" target="_blank">vue-loader</a></li>
      <li><a href="https://github.com/vuejs/awesome-vue" target="_blank">awesome-vue</a></li>
    </ul>
    <h2>SMEO BARCODE</h2>
    <div>BARCODES: {{barcodeArr}}</div>
    <div>
      <span>CURRENT BARCODE: {{barcode}}</span>
      <button @click="clearBarcode">CLEAR</button>
    </div>

  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      barcode: '',
      barcodeArr: []
    }
  },
  created: function () {
    window.addEventListener('keypress', this.handleKeys)
//    chrome.printerProvider.onPrintRequested.addListener(this.printCallback)
  },
  methods: {
    handleKeys: function (e) {
      if (e.keyCode === 13) {
        this.submitBarcode()
        return
      }
      this.barcode = this.barcode + e.key
    },
    clearBarcode: function () {
      this.barcode = ''
    },
    submitBarcode: function () {
      this.barcodeArr.push(this.barcode)
      // this.printMe()
      this.barcode = ''
    },
    printMe: function () {
      const myWindow = window.open('', '', 'width=200,height=100')
      myWindow.document.write("<p>'Steph printed this'</p>")
      myWindow.document.close()
      myWindow.focus()
      myWindow.print()
    }
  },
  beforeDestroy: function () {
    window.removeEventListener('keypress', this.handleKeys)
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
