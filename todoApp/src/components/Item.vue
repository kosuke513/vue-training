<template>
  <div class="item-outline">
    <slot name="first" :slotProp="discription"></slot>
    <slot name="second" :slotProp="discription"></slot>
    <h3 v-show="formHidden">{{ title }}
      <input v-model.number="point" v-show="!pointHidden" @blur="emitPoint">
      <span v-show="pointHidden" @click="switchPointHidden">{{ point }}</span>
    </h3>
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
  props: ['title','text','date'],
  data () {
    return {
      formHidden: true,
      oldPoint: 0,
      point: 0,
      pointHidden: true,
      discription: {
        text: 'modifyを押すとlistを編集することができます。',
        item: '数字はClickすると編集することができます'
        }
    }
  },
  methods: {
    switchtextHidden: function () {
      return this.formHidden = !this.formHidden
    },
    switchPointHidden: function () {
      this.oldPoint = this.point
      return this.pointHidden = !this.pointHidden
    },
    emitPoint: function(){
      this.$emit('total-point', this.oldPoint, this.point)
      return this.pointHidden = !this.pointHidden
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