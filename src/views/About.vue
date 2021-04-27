<template>
  <div class="about">
    <h1>Min</h1>
    <input v-model.number="minA">
    <input v-model.number="minB">
    <button v-on:click="min()">Min</button>
    {{minAnswer}}

    <h1>Max</h1>
    <input v-model.number="maxA">
    <input v-model.number="maxB">
    <button v-on:click="max()">max</button>
    {{maxAnswer}}

    <h1>Abs</h1>
    <input v-model.number="ab">
    <button v-on:click="abA()">abs</button>
    {{absAnswer}}

    <h1>isEven</h1>
    <input v-model.boolean="a">
    <button v-on:click="isEvenA()">isEven</button>
    {{isEvenAnswer}}

    <h1>min3</h1>
    <input v-model.number="aa">
    <input v-model.number="bb">
    <input v-model.number="cc">
    <button v-on:click="min3()">Min3</button>
    {{min3Answer}}

    <h1>max3</h1>
    <input v-model.number="aaa">
    <input v-model.number="bbb">
    <input v-model.number="ccc">
    <button v-on:click="max3()">Max3</button>
    {{max3Answer}}

  </div>
</template>

<script>

function min() {
  if (this.minA < this.minB){
    this.minAnswer = this.minA;
  } else {
    this.minAnswer = this.minB;
  }
}

function max() {
  if (this.maxA > this.maxB) {
    this.maxAnswer = this.maxA;
  } else {
    this.maxAnswer = this.maxB;
  }
}

function abA() {
  if (this.ab < 0) {
    this.absAnswer = -this.ab;
  } else {
    this.absAnswer = this.ab;
  }
}

function isEvenA() {
  if (this.a % 2 === 0) {
    this.isEvenAnswer = true;
  } else {
    this.isEvenAnswer = false;
  }
}

function min3() {
  if (this.aa >= this.bb) {
    if (this.bb >= this.cc) {
      this.min3Answer = this.cc;
    } else {
      this.min3Answer = this.bb;
    }
  } else if (this.aa <= this.cc) {
    this.min3Answer = this.aa;
  } else {
    this.min3Answer = this.cc;
  }
}

function max3() {
  if (this.aaa <= this.bbb) {
    if (this.bbb <= this.ccc) {
      this.max3Answer = this.ccc;
    } else {
      this.max3Answer = this.bbb;
    }
  } else if (this.aaa >= this.ccc) {
    this.max3Answer = this.aaa;
  } else {
    this.max3Answer = this.ccc;
  }
}

export default {
  data: function (){
    return {
      'minA': 0,
      'minB': 0,
      'minAnswer': 0,
      'maxA': 0,
      'maxB': 0,
      'maxAnswer': 0,
      'ab': 0,
      'absAnswer': 0,
      'a': 0,
      'isEvenAnswer': true,
      'min3Answer': 0,
      'aa': 0,
      'bb': 0,
      'cc': 0,
      'max3Answer': 0,
      'aaa': 0,
      'bbb': 0,
      'ccc': 0,
    }
  },
  methods: {
    'min': min,
    'max': max,
    'abA': abA,
    'isEvenA': isEvenA,
    'min3': min3,
    'max3': max3
  }
}

</script>