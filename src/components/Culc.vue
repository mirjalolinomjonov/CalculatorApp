<template>
  <div
    class="p-3"
    style="max-width: 400px; margin: 50px auto; background: #234"
  >
    <!-- calculator result start-->
    <div
      class="
        w-full
        rounded
        m-1
        p-3
        text-right
        lead
        font-weight-bold
        text-white
        bg-vue-dark
      "
    >
      {{ calculatorValue || 0 }}
    </div>
    <!-- calculator result end -->

    <!-- calculator buttons start -->
    <div class="row no-gutters">
      <div class="col-3" v-for="n in calculatorElements" :key='n'>
        <div @click="action(n)" :class="{'bg-vue-green':['C', '*', '/', '-', '+', '%', '='].includes(n)}" class="lead text-center text-white m-1 py-3 bg-vue-dark rounded hover-class">
        {{n}}
        </div>
      </div>
    </div>
    <!-- calculator buttons end -->
  </div>
</template>

<script>
export default {
  name: "Culc",

  data() {
    return {
      calculatorValue: '',
      operator: null,
      previousCalculatorValue: '',
      calculatorElements: [
        "C",
        "*",
        "/",
        "-",
        7,
        8,
        9,
        "+",
        4,
        5,
        6,
        "%",
        1,
        2,
        3,
        "=",
        0,
        ".",
      ],
    };
  },

  methods: {
    // Append value
    action(n) {
      if(!isNaN(n) || n === '.') {
        this.calculatorValue += n + "";
      } else 

      if (n === 'C'){
        this.calculatorValue = ''
      } else 

      if(n === '%') {
        this.calculatorValue /= 100
      } else 

      if(['/','*','-','+'].includes(n)){
        this.operator = n;
        this.previousCalculatorValue = this.calculatorValue
        this.calculatorValue = ''
      } else

      if(n === '=') {
        this.calculatorValue = eval(
          this.previousCalculatorValue + this.operator + this.calculatorValue
        );

        this.previousCalculatorValue = '';
        this.operator = null
      }
    }
  }
};
</script>

<style lang="scss">
.bg-vue-dark {
  background-color: #31475e;
}

.bg-vue-green {
  background-color: #3fb984;
}
.text-right {
  text-align: right;
}

.font-weight-bold {
  font-weight: bold !important;
}

.hover-class:hover {
  cursor: pointer;
  background-color: #3d5875;
}
</style>
