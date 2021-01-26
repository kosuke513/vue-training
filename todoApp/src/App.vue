<template>
  <div id="app">
    <headerView></headerView>
    <p>こんにちは</p>
    <router-view/>
    <div class="item-container">
      <todoItem></todoItem>
      <todoItem></todoItem>
      <todoItem></todoItem>
    </div>
    <footerView></footerView>
  </div>
</template>

<script>
import headerView from './components/Header.vue'
import todoItem from './components/Item.vue'
import footerView from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    headerView,
    todoItem,
    footerView
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


</style>
