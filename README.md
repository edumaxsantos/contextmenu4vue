# contextmenu4vue

> Context Menus with [Vue.js](https://github.com/vuejs/vue) (vue2.4)

# Warning
**2018-12-17 - I'll be updating this project. It has been a long time since I created this repo and now I think it's time to get back to it.**
---
**This component is still being written so if it's not working the way you want, I'm still working on it.**


# Menu
* [Build Setup](#build-setup)
* [How to use](#how-to-use)
* [Basic Context Menu](#basic-context-menu)
* [License](#license)

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
- Add the import below to your *App.vue*
``` javascript 
    import contextMenu from './components/contextMenu' 
``` 

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

## Basic Context Menu
You only need to send an object to the component, so it will generate your own context menu.
> But you to structure it?
>
Okay, so there's only one key from your object that's actually needed. It's the ``` items ``` key.
> Why is it needed?
>
It's where you're going to place your items for the context menu. If you don't set it, there's no list to be rendered.
> Alright. So how does this *items* key should look like?
``` javascript
items: [{
  text: 'OP1' // text will hold the name of your item at your context menu.
  icon: null // it's still not being used. so don't mind it
  func() {}  // func() is where you'll send what your item should do when it's clicked
}]
```
That's basically everything you need to set. *items* must be inside your **myMenu** (you can name it anything you want) object that's being passed as prop. Just check [How to use](#how-to-use)


## License

[MIT](http://opensource.org/licenses/MIT)
