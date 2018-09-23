# VueJS Components

It has 3 parts:

* Template (html)
* Logic (javascript)
* Style (css)

```html
<template>
</template>

<script>
</script>

<style scoped>
</style>
```

## How to use Components

* First, you have to import the component:

```js
import HelloWorld from './components/HelloWorld.vue'
```

* Register the component

```js
export default {
  name: 'app',
  components: {
    HelloWorld
  }
}
```

* Now, you can use it on your template. The component is called as if it was an HTML Tag

```html
<template>
  <div>
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>
```