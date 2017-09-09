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
        },
        /*font: {
          family: 'Roboto',
          size: 12
        },*/
        items: [{
          text: 'op1',
          icon: null,
          func() {
            console.log('im func 1');
          }
        }, {
          text: 'op2',
          func() {
          }
        }, {
          text: 'third op',
          icon: null,
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
