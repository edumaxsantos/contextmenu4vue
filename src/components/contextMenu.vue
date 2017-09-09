<template>
  <div class="context-menu">
    <ul class="context-menu-list" :class="[classes.color, {'rounded': classes.rounded}]">
      <li v-for="op in menu.items" :key="op.text" class="context-menu-list-item" @click="op.func">
      {{op.text}}
      {{op.description}}
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
      classes: {
        color: '',
        rounded: ''
      },
      myMenu: '',
      default: {
        font: {
          family: 'Arial, serif',
          size: 12
        },
        class: {
          color: 'primary',
          rounded: true
        }
      }
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
    },

    setClasses() {
      if (this.menu.hasOwnProperty('class')) {
        (this.menu.class.hasOwnProperty('color') && this.menu.class.color !== '' )
          ? this.classes.color = this.menu.class.color
          : this.classes.color = this.default.class.color;
        (this.menu.class.hasOwnProperty('rounded'))
          ? this.classes.rounded = this.menu.class.rounded
          : this.classes.rounded = this.default.class.rounded
      } else {
        this.menu.class = {};
        this.setClasses();
      }
    },

    setFont() {
      if (this.menu.hasOwnProperty('font')) {
        (this.menu.font.hasOwnProperty('family') && this.menu.font.family !== '' )
          ? this.myMenu.style.fontFamily = this.menu.font.family 
          : this.myMenu.style.fontFamily = this.default.font.family;
        (this.menu.font.hasOwnProperty('size') && this.menu.font.size !== '') 
          ? this.myMenu.style.fontSize = this.menu.font.size + 'px' 
          : this.myMenu.style.fontSize = this.default.font.size + 'px';
      } else {
        this.menu.font = {};
        this.setFont();
      }
      
    }
  },
  mounted() {
    this.myMenu = document.querySelector('.context-menu-list');
    document.addEventListener('contextmenu', (event) => {
      event.preventDefault();
      this.x = event.clientX;
      this.y = event.clientY;
      this.setFont();
      this.setClasses();
      this.setPositions();
      this.showMenu();
    });
    document.addEventListener('click', (event) =>{
      this.hideMenu();
    });
    document.addEventListener('scroll', (event) => {
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
  box-shadow: 5px 5px 0px -3px rgba(200,200,200,0.5); 
}


.primary {
  background-color: rgb(240,240,240);
  color: rgba(25, 25, 25, 0.8);
  border: 1px solid rgba(25, 25, 25, 0.2);
}

.primary .context-menu-list-item:hover {
  background-color: rgba(200,200,200, 0.85);
}

.secondary {
  background-color: rgb(50, 50, 50);
  color: rgba(250, 250, 250, 0.9);
  border: 1px solid rgba(200, 200, 200, 0.8);
}

.secondary .context-menu-list-item:hover {
  background-color: rgba(150, 150, 150, 0.75);
}

.emerald {
  background-color: rgb(46, 204, 113);
  color: rgba(236, 240, 241,1.0);
  border: 1px solid rgba(39,174, 96, 0.6);
}

.emerald .context-menu-list-item:hover {
  background-color: rgb(39, 174, 96);
}

.blue {
  background-color: rgb(52, 152, 219);
  color: rgba(236, 240, 241, 1);
  border: 1px solid rgba(41, 128, 185, 0.8);
}

.blue .context-menu-list-item:hover {
  background-color: rgb(41, 128, 185);
}

.context-menu-list-item {
  margin: 2px 0 5px 0;
  box-sizing: border-box;
  padding: 2px 10px 2px 30px;
}

.context-menu-list-item:last-child {
  margin: 2px 0;
}

.context-menu-list-item:hover {
  background: orange;
  cursor: pointer;
}
</style>
