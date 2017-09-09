<template>
  <div id="app">
    <select v-model="clas.color">
    <option v-for="op in themes" :key="op.name" :value="op.name" >{{op.name}}</option>
    </select>
    <input type="checkbox" v-model="clas.rounded">Rounded?
    <div style='width: 1000px; height: 1000px;'></div>
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
      clas: {
        color: '',
        rounded: false
      },
      myMenu: {
        class: {},
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
  },
  mounted() {
    this.myMenu.class = this.clas;
  }
}
</script>

<style>

</style>
