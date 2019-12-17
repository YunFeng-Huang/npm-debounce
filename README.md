# debounce

> A Vue.js project

## Build Setup

``` bash

npm i yfzw-vue-debounce

import vDebounce from 'yfzw-vue-debounce'
Vue.use(vDebounce)

<v-debounce
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
</v-debounce>
```