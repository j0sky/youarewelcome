<template>
  <div id="app">
    <Page />
    <Chat />
  </div>
</template>

<script>
import Page from './components/Page.vue'
import Chat from './components/Chat.vue'

export default {
  name: 'app',
  components: {
    Page,
    Chat
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
