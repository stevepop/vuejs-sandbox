<template>
  <div id="app">
    <div class="container">
      
        <div class="d-flex justify-content-center mt-4">
          <hello></hello>
        </div>
    </div>
  </div>
</template>

<script>
import Hello from './components/Hello'

export default {
  name: 'app',
  components: {
    Hello
  }
}
</script>

<style lang="scss">
@import './assets/styles/custom-bootstrap.scss';
@import '../node_modules/bootstrap/scss/bootstrap.scss';
</style>
