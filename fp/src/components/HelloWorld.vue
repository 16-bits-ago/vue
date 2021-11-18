<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <input  type="number" placeholder="operand1" v-model.number="operand1"/>
    <input  type="number" placeholder="operand2" v-model.number="operand2" />
    <br />
    {{ result }}
    <br />
    <button v-on:click="result = operand1 + operand2">+</button>
    <button @click="result = operand1 - operand2">-</button>
    <button @click="mul">*</button>
    <button @click="div">/</button>
    <button @click="pow">✓</button>

    <div id="wrapper">
      <div v-on:click="seen = !seen">
        <input type="checkbox" id="checkbox" v-model="checked" />
        <label for="checkbox">{{
          checked ? "Скрыть клаву" : "Показать клаву"
        }}</label>
      </div>
      <div v-if="seen">
        <!-- <button @click="1">1</button>
        <button @click="2">2</button>
        <button @click="3">3</button>
        <br />
        <button @click="4">4</button>
        <button @click="5">5</button>
        <button @click="6">6</button>
        <br />
        <button @click="7">7</button>
        <button @click="8">8</button>
        <button @click="9">9</button>
        <button @click="0">0</button> -->
        <button v-for="(num,idx) in numbers" :key="idx" >{{num}}</button>
        <br />
        <button>delete</button>
      </div>
    </div>
    <div>
      <input type="radio" id="one" value="Один" v-model="picked" />
    <label> operand1</label>
    <br />
    <input type="radio" id="two" value="Два" v-model="picked" />
    <label for="two">operand2</label>
    <br />
    <span>Выбрано: {{ picked }} </span>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
  data() {
    
    return {
      numbers: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9,],
      message: "hello VUE",
      result: 0,
      operand1: 0,
      operand2: 0,
      seen: false,
      checked: false,
      picked: true,
    };
  },
  methods: {
    onChange(str, event) {
      console.log(str, event);
    },
    mul() {
      this.result = this.operand1 * this.operand2;
    },
    div() {
      const { operand1, operand2 } = this;
      this.result = operand1 * operand2;
    },
    pow() {
      const { operand1, operand2 } = this;
      this.result = operand1 ** operand2;
    },
    onChangeInput(str, event) {
      this.operand1 = event.target.value;
    },

  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
