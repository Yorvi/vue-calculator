<template>
  <div class="calculator">
    <div class="display">
      {{current || '0'}}
    </div>
    <div class="btn">C</div>
    <div class="btn">+/-</div>
    <div class="btn">%</div>
    <div class="btn operator">&divide;</div>
    <div class="btn">7</div>
    <div class="btn">8</div>
    <div class="btn">9</div>
    <div class="btn operator">&times;</div>
    <div class="btn">4</div>
    <div class="btn">5</div>
    <div class="btn">6</div>
    <div class="btn operator">-</div>
    <div class="btn">1</div>
    <div class="btn">2</div>
    <div class="btn">3</div>
    <div class="btn operator">+</div>
    <div class="zero btn">0</div>
    <div class="btn">.</div>
    <div class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      current: '',
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
}
.display {
  grid-column: 1/5;

  background-color: #33475F;
  color: white;
  margin: 5px;
  border-radius: 10px;
  text-align: end;
  padding: 5px 15px;
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
}
.operator {
  background-color: #00C180;
}
</style>
