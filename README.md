# vue-contextmenu

> Context Menus with Vue.js (vue2.4)

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```
## How to use

The same way you'd add any other vue component.
- Copy *contentMenu.vue* to your components folder.
- Add 
``` javascript 
    import contextMenu from './components/contextMenu' 
``` 
to your *App.vue*
- Don't forget to also add it to your app's components. 
``` javascript
components: {
    contextMenu
  } 
  ```
- And add your tag anywhere
``` html
<context-menu :menu="myMenu"></context-menu>
```
  
  ## License

[MIT](http://opensource.org/licenses/MIT)