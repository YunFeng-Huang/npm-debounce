<template>
  <div id="app">
    <Debounce
      :page="page"
      :pageSize="pageSize"
      :total="total"
      @debounce="_scroll($event)"
      class="scroll" ref="debounce">
      <li v-for="(item, index) in [1,2,3,4,5,6,7,8,9,0,11,2,3,4,5,6,7,89,0,1,2,3,4,56,7]" :key="index">
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
        <div>1</div>
      </li>
    </Debounce>
  </div>
</template>

<script>
import Debounce from './compontents/debounce'; // 引入
export default {
  name: 'app',
  data () {
    return {
      page: 1,
      pageSize: 10,
      total: 0,
    }
  },
  methods:{
    _scroll() {
      this.page++;
      console.log(this.page)
    },
  },
  components:{
    Debounce
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;

  padding: 0;
}
.scroll{
  height: 200px;
    overflow: auto;
}
</style>
