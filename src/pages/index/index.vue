<template>
  <div class="container">
    <div class="message" @click="clickHandle">{{msg}}</div>
    <div :class="['flexbox',alignItem]">
      <FlexCom pct="80" />
      <FlexCom pct="100" />
      <FlexCom pct="160" />
      <FlexCom pct="40" />
    </div>
    <div>
      <button v-for="item in aligns" :key="item.key" @click="changeAlign(item.value)">{{item.value}}</button>
    </div>
  </div>
</template>

<script>
import FlexCom from '../../components/flex-com'
export default {
  components: {
    FlexCom
  },
  data () {
    return {
      msg: 'Hello Click Me',
      alignItem: 'flex-end',
      aligns: [
        { key: 0, value: 'flex-start' },
        { key: 1, value: 'flex-end' },
        { key: 2, value: 'center' }
      ]
    }
  },
  methods: {
    clickHandle () {
      this.msg = 'Welcome to Taki\'s first mpvue Project'
    },
    changeAlign (align) {
      this.alignItem = align
    }
  }
}
</script>

<style scoped>
.message {
  color: #00b26a;
  padding: 10px;
  text-align: center;
}
.flexbox {
  background: #fff;
  border: 1px solid #ddd;
  min-height: 300px;

  display: flex;
  justify-content: space-between;
}
.flexbox.flex-start {
  align-items: flex-start;
}
.flexbox.flex-end {
  align-items: flex-end;
}
.flexbox.center {
  align-items: center;
}
</style>