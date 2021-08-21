<template>
  <div id="app">
    <culc></culc>
    <router-view />
  </div>
</template>

<script>
import Culc from './components/Culc'
export default {
  components: {Culc}
}
</script>

<style lang="scss">
body {
  background-color: #31475e;
}

</style>
