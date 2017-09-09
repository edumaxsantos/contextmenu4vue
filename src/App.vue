<template>
  <div id="app">
    <select v-model="myMenu.class.color">
    <option v-for="op in themes" :key="op.name" :value="op.name" >{{op.name}}</option>
    </select>
    <input type="checkbox" v-model="myMenu.class.rounded">Rounded?
    <context-menu :menu="myMenu"></context-menu>
  </div>
</template>

<script>
import contextMenu from './components/contextMenu'

export default {
  name: 'app',
  components: {
    contextMenu
  },
  data() {
    return {
      themes: [{
        name: 'primary'
      }, {
        name: 'secondary'
      }, {
        name: 'emerald'
      }, {
        name: 'blue'
      }],
      myMenu: {
        class: {
          color: 'primary',
          rounded: false
        },
        ops: [{
          text: 'op1',
          func() {
            console.log('oi');
          }
        }, {
          text: 'op2',
          func() {

          }
        }]
      }
    }
  }
}
</script>

<style>

</style>
