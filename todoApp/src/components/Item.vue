<template>
  <div class="item-outline">
    <h3 v-show="formHidden">{{ title }}</h3>
    <input v-show="!formHidden" v-model="title">
    <div class="item-container">
      <div class="item-left">
        <p>詳細</p>
        <p v-show="formHidden">{{text}}</p>
        <textarea v-show="!formHidden" :placeholder="text" v-model="text"></textarea>
      </div>
      <div class="item-right">
        <p>締め切り日
          <span  v-show="formHidden"> {{ date }}</span>
          <input v-show="!formHidden" v-model="date"/></p>
        <div class="btn-container">
          <button @click="switchtextHidden">modify</button>
          <button>done</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      title: 'タイトル',
      text: 'テキスト',
      date: '2021/1/12',
      formHidden: true
    }
  },
  methods: {
    switchtextHidden: function () {
      return this.formHidden = !this.formHidden
    }
  }
}
</script>

<style scoped>
  .item-outline{
    border: solid 1px gray;
    width: 75%;
    margin: 15px auto;
  }
  h3 {
    margin-left: 70px;
    text-align: left;
  }
  .item-container {
    display: flex;
  }
  .item-left {
    text-align: left;
    width: 500px;
  }
  .item-left p {
    margin-bottom: 5px;
    margin-left: 50px;
  }
  .item-left textarea {
    margin-left: 50px;
    width: 75%;
  }
  .item-right {
    width: 500px;
    margin: auto 0;
  }
  .item-right p {
    margin-top: 30px;
    display: inline;
  }
  .item-right input {
    display: inline-block;
    margin-left: 30px;
    width: 50%;
  }
  .button-container {
    margin-top: 30px;
  }
  button {
    display: inline-block;
    margin: 5px;
    font-size: 18px;
    color: white;
    background-color: blue;
    border: none;
    width: 90px;
  }
</style>