<script>
  export default{
    data(){
      return{
        previous: null,
        current: '',
        operator: null,
        operatorClicked: false,
      }
    },
    methods: {
      clear(){
        this.current = ''
      },
      append(number){
        if(this.operatorClicked){
          this.current = ''
          this.operatorClicked = false
        }
        this.current = `${this.current}${number}`
      },
    add(){
      this.operator = (a,b) => (b+a)
      this.previous = this.current
      this.operatorClicked = true
    },
    subtract(){
      this.operator = (a,b) => (b-a)
      this.previous = this.current
      this.operatorClicked = true
    },
    multiply(){
      this.operator = (a,b) => (b*a)
      this.previous = this.current
      this.operatorClicked = true
    },
    divide(){
      this.operator = (a,b) => (b/a)
      this.previous = this.current
      this.operatorClicked = true
    },
    equal(){
      this.current = `${this.operator(
        parseFloat(this.current), 
        parseFloat(this.previous))}`;
      this.previous = null
    }
    }
  }
</script>

<template>
  <div class="calculator">
    <div class="display">{{current || '0'}}</div>
    <button type="button" @click="add" class="btn operator">+</button>
    <button type="button" @click="subtract" class="btn operator">-</button>
    <button type="button" @click="multiply" class="btn operator">x</button>
    <button type="button" @click="divide" class="btn operator">÷</button>

    <button type="button" @click="append('7')" class="btn">7</button>
    <button type="button" @click="append('8')" class="btn">8</button>
    <button type="button" @click="append('9')" class="btn">9</button>

    <button type="button" @click="equal" class="compute btn">=</button>

    <button type="button" @click="append('4')" class="btn">4</button>
    <button type="button" @click="append('5')" class="btn">5</button>
    <button type="button" @click="append('6')" class="btn">6</button>

    <button type="button" @click="append('1')" class="btn">1</button>
    <button type="button" @click="append('2')" class="btn">2</button>
    <button type="button" @click="append('3')" class="btn">3</button>

    <button type="button" @click="append('0')" class="btn">0</button>
    <button type="button" @click="clear" class="clear btn">C</button>
  </div>
</template>

<style scoped>
  .calculator{
    margin: 0 auto;
    width: 500px;
    font-size: 40px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: minmax(50px, auto);
  }

  .display{
    grid-column: 1 / 5;
    border: 1px solid grey;
    background-color: black;
    color: darkgray;
  }
  .compute{
    grid-row: 3 / 7;
    grid-column: 4;
  }
  .clear{
    grid-column: 2 / span 2;
  }

  .btn{
    background-color: darkgrey;
    border: 1px solid grey;
  }
  .operator{
    background-color: #007bff;
  }
</style>
