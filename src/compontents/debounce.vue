<template>
  <div class="scroll" ref="debounce_w" :class="{'overhidden':spinShow}">
    <ul ref="debounce_child">
      <slot></slot>
      <div class="message">{{message}}</div>
      <!-- <transition name="fade">
        <div v-if="spin" class="message">{{message}}</div>
      </transition> -->
    </ul>
    <!-- <Spin size="large" fix v-if="spinShow"></Spin> -->
  </div>
</template>

<script>
export default {
  name:'vDebounce',
  props: {
    wait: {
      type: Number,
      default: 1000,
    },
    scrollTop: {
      type: Number,
      default: 400,
    },
    page: {
      type: Number,
      default: 1,
    },
    pageSize: {
      type: Number,
      default: 10,
    },
    total: {
      type: Number,
      default: 1,
    },
  },
  data() {
    return {
      spinShow: false,
      spin: false,
      message: '-------- 已经到底啦 --------',
    };
  },
  mounted() {
    this.$nextTick(() => {
      this.$refs.debounce_w.addEventListener('scroll', this.throttle(() => {
        this.$emit('debounce');
      }, this.wait));
    });
  },

  methods: {
    throttle(fn, wait) {
      let previous = 0;
      return () => {
        let now = +new Date();
        let scrollTop = this.$refs.debounce_child.clientHeight - this.$refs.debounce_w.clientHeight - this.$refs.debounce_w.scrollTop;
        if (now - previous > wait && scrollTop < this.scrollTop && this.page * this.pageSize < this.total) {
          previous = now;
          fn();
        }
      };
    },
  },
  beforeDestroy() {
    this.$refs.debounce_w.removeEventListener('scroll', this.throttle(() => { this.$emit('debounce'); }, this.wait));
  },
};
</script>
<style  scoped>
  .message{
    text-align:center
  }
  .overhidden{overflow:hidden}
</style>
