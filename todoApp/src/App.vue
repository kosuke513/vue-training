<template>
  <div id="app">
    <headerView></headerView>
    <p>こんにちは</p>
    <h2>合計：{{ totalPoint }}</h2>
    <div class="item-container">
      <todoItem :title="title" :text="text" :date="date" @total-point="countTotalPoint">
        <template v-slot:first="slotProps">
          <p>{{ slotProps.discription.text }}</p>
        </template>
      </todoItem>
      <todoItem :title="title" :text="text" :date="date" @total-point="countTotalPoint">
        <template #second="{discription}">
          <p>{{ discription.item }}</p>
        </template>
      </todoItem>
      <todoItem :title="title" :text="text" :date="date" @total-point="countTotalPoint"></todoItem>
      <todoItem :title="title" :text="text" :date="date" @total-point="countTotalPoint"></todoItem>
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
  },
  data() {
    return {
      totalPoint: 0,
      title: 'タスクのタイトル',
      text: 'タスクの詳細',
      date: '2020/1/26'
    }
  },
  methods: {
    countTotalPoint: function(value1, value2){
      return this.totalPoint = this.totalPoint - value1 + value2
    }
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
