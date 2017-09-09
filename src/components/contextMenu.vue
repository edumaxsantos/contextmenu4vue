<template>
  <div class="context-menu">
    <ul class="context-menu-list" :class="[menu.class.color, {'rounded': menu.class.rounded}]">
      <li v-for="op in menu.ops" :key="op.id" class="context-menu-list-item" @click="op.func">
      {{op.text}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'contextMenu',
  props: {
    menu: {
      type: Object
    }
  },
  data () {
    return {
      x: '',
      y: '',
      myMenu: ''
    }
  },
  methods: {
    setPositions() {
      this.myMenu.style.top = this.y + 'px';
      this.myMenu.style.left = this.x + 'px';
    },
    showMenu() {
      this.myMenu.style.display = 'inline-block';

    },
    hideMenu() {
      this.myMenu.style.display = 'none';
    }
  },
  mounted() {
    this.myMenu = document.querySelector('.context-menu-list');
    document.addEventListener('contextmenu', (event) => {
      event.preventDefault();
      this.x = event.clientX;
      this.y = event.clientY;
      this.setPositions();
      this.showMenu();
    });
    document.addEventListener('mousedown', (event) =>{
      this.hideMenu();
    });

  }
}
</script>

<style scoped>

.rounded {
  border-radius: 5px;
}

.context-menu-list {
  display: none;
  position: fixed;
  list-style: none;
  width: fit-content;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
  border: 1px solid #bdc3c7;
}

.primary {
  background-color: rgba(225,225,225,0.5);
}

.primary .context-menu-list-item:hover {
  background-color: rgba(200,200,200, 0.85);
}

.secondary {
  background-color: rgba(10, 10, 10, 0.75);
  color: rgba(250, 250, 250, 0.9);
}

.secondary .context-menu-list-item:hover {
  background-color: rgba(150, 150, 150, 0.75);
}

.emerald {
  background-color: rgba(46, 204, 113,1.0);
  color: rgba(236, 240, 241,1.0);
}

.emerald .context-menu-list-item:hover {
  background-color: rgba(39, 174, 96,1.0);
}

.context-menu-list-item {
  margin: 2px 0;
  box-sizing: border-box;
  padding-left: 20px;
  padding-right: 10px;
}

.context-menu-list-item:hover {
  background: orange;
  cursor: pointer;
}
</style>
