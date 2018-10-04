<template>

  
  <div>
    <h1>Welcome to my Vue Calculator</h1>
    <div class="calculator">
      <div class="display">
        {{current || '0'}}
      </div>

      <div @click="clear" class="btn">C</div>
      <div @click="sign" class="btn">+/-</div>
      <div @click="percent" class="btn">%</div>
      <div @click="divide" class="btn operator">&divide;</div>

      <div @click="append('7')" class="btn">7</div>
      <div @click="append('8')" class="btn">8</div>
      <div @click="append('9')" class="btn">9</div>
      <div @click="times" class="btn operator">&times;</div>

      <div @click="append('4')" class="btn">4</div>
      <div @click="append('5')" class="btn">5</div>
      <div @click="append('6')" class="btn">6</div>
      <div @click="minus" class="btn operator">-</div>

      <div @click="append('1')" class="btn">1</div>
      <div @click="append('2')" class="btn">2</div>
      <div @click="append('3')" class="btn">3</div>
      <div @click="plus" class="btn operator">+</div>

      <div @click="append('0')" class="zero btn">0</div>
      <div @click="dot" class="btn">.</div>
      <div @click="equal" class="btn operator">=</div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      previous: null,
      current: '',
      operator: null,
      operatorClicked: false,
    }
  },
  methods: {
    clear() {
      this.current = '';
    },
    sign() {
      this.current = this.current.charAt(0) === '-' ? this.current.slice(1) : `-${ this.current }`;
    },
    percent() {
      this.current = `${parseFloat( this.current ) / 100}`;
    },
    append(number) {
      if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      this.current = `${this.current}${number}`;
    },
    dot() {
      if ( this.current.indexOf('.') === -1 ) {
        this.append('.');
      }
    },
    setPrev() {
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide() {
      this.operator = ( a, b ) => a / b;
      this.setPrev();
    },
    times() {
      this.operator = ( a, b ) => a * b;
      this.setPrev();
    },
    minus() {
      this.operator = ( a, b ) => a - b;
      this.setPrev();
    },
    plus() {
      this.operator = ( a, b ) => a + b;
      this.setPrev();
    },
    equal() {
      this.current = `${this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      )}`;
      this.previous = null;    
    }
  }
}
</script>

<style scoped>
div.calculator {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);

  font-size: 40px;
  width: 400px;
  margin: 0 auto;
  background-color: #EEF0F3;
  border: 1px solid black;
  border-radius: 2px;
  box-shadow: 1px 1px 10px #555553;
}
.display {
  grid-column: 1/5;

  background-color: #33475F;
  color: white;
  margin: 5px;
  padding: 50px 15px 0;
  border-radius: 10px;
  text-align: end;
}
.zero {
  grid-column: 1/3;
}
.btn {
  background-color: #FEFFFE;
  margin: 5px;
  border: 1px solid #33475F;
  border-radius: 10px;
  color: #33475F;
  box-shadow: 1px 1px 2px #555553;
}
.btn:hover {
  background-color: #49D191;
  cursor: pointer;
}
.operator {
  background-color: #00C180;
  box-shadow: 1px 1px 2px #5cf776;
}
</style>
