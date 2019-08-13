<template>
  <div :class="['box','box-justify-' + justify]" :style="{height: percent + 'px'}" @click="check">
    <div class="plusminus">
        <div class="plus" @click="minus">-</div>
        <div class="minus" @click="plus">+</div>
        <div class="score">{{percent / 2}}%</div>
    </div>   
  </div>
</template>

<script>

export default {
  props: {
    jfy: {
      type: String,
      default: 'flex-start'
    },
    pct: {
      type: Number,
      default: 80
    }
  },
  data () {
    return {
      justify: this.jfy,
      percent: this.pct
    }
  },
  methods: {
    check () {
      console.log(this.justify, this.percent)
    },
    plus () {
      let p = parseInt(this.percent)
      this.percent = p <= 180 ? p + 20 : p
    },
    minus () {
      let p = parseInt(this.percent)
      this.percent = p >= 20 ? p - 20 : p
    }
  }
}
</script>

<style scoped>
.box {
  width: 40px;
  background: #00b26a;
  margin: 50px 5px 5px 5px;
  text-align: right;
  justify-content: space-between;
}

.box .plusminus{
  display: absolute;
  margin-top: -45px;
}
.box .plus,
.minus {
  display: inline-block;
  height: 20px;
  width: 20px;
  color: #00b26a;
  border: 1px solid #00b26a;
  text-align: center;
  box-sizing: border-box;
}

.box .score{
  font-size: 12px;
  color:#00b26a;
  text-align: center;
}
</style>