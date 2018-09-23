# Commands

## Run Server

This command will run a test server and refresh your page everytime you update your project.

```cmd
npm run serve
```

## Build Application

This command will create a single file html application. All files will be placed within dist folder. Distribute only the content inside that folder.

```cmd
npm run build
```

## Vue Structure

* public
  * favicon.ico
  * index.html
* src
  * assets
  * components
  * App.vue
  * main.js
* babel.config.js
* package-lock.json
* package.json

usage example:

* v-on:click="functionName"
* v-bind:disabled="varName"

```html
<button type="button" name="button" v-on:click="changeName" v-bind:disabled="btnState">Change Name</button>
```

```js
export default {
  data() {
    return {
      name: "Coursetera",
      varName: true,
    }
  }
}
```

## Directives

Here is a list of directives that you can use:

* v-text
* v-html
* v-if

```html
<p v-if="skills.length > 1">You have mor than 1 skills</p>
<p v-else>You have less than or equal to 1 skill</p>
```

* v-else-if
* v-for

```html
<ul>
  <li v-for="(data, index) in skills" :key='index'>{{ index }} . {{ data.skill }}</li>
</ul>
```

```js
data() {
  return {
    skills : [
      { "skill": "Vue.js"},
      { "skill": "Frontend Developer"},
    ]
  }
}
```

* v-on
* v-bind

Allows you to controll css classes dynamically.

Im this example, you'll print alert inside the class, when showAlert is true:

```html
<template>
  <div>
    <div v-bind:class="{alert: showAlert}">
    <div v-bind:class="{alert: showAlert, 'another-class' : showClass }">
  </div>
</template>

<script>
export default {
  data() {
    return {
      showAlert: false,
      showClasss: true
    }
  }
}
</script>

<style scoped>
  .alert {
    background-color: yellow;
    width: 100%;
    height: 30px;
  };

  .another-class {
    border: 5px solid black;
  }
</style>
```

* v-model

You can send information from logic to template and vice-versa using v-model

```html
<input type="text" placeholder="Enter a skill you have..." v-model="skill">
<input type="checkbox" id="checkbox" v-model="checked">

<script>
export default {
  data() {
    return {
      skill: '',
      checked: true
    }
  }
}
</script>
```

* v-pre
* v-cloak
* v-once

## CSS

* scoped

It means that the style will be only applied to the actual component

```css
<style scoped>
</style>
```

you can also use a css file

```html
<style src="./Skills.css" scoped></style>
```

## Animation

Using Animate.css library

## Routing

Using vue-router library.

create a file router.js inside src folder, with the following content:

```js
import Vue from 'vue'
import Router from 'vue-router'

<!-- Pages -->
import Skills from './components/Skills.vue'
import About from './components/About.vue'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'skills',
      component: Skills
    },
    {
      path: '/about/:name',
      name: 'about',
      component: About
    }
  ]
})
```

You have to change a little bit main.js file:

```js
import Vue from 'vue'
import App from './App.vue'
import VeeValidate from 'vee-validate';

<!-- import the actual router -->
import router from './router'

Vue.use(VeeValidate);
Vue.config.productionTip = false

new Vue({
  router, // register the imported router here
  render: h => h(App)
}).$mount('#app')
```

Also, you have to define where to place the router content. In this case, we'll use App.vue file:

```html
<template>
  <div id="app">
    <!-- Simple navigation example -->
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>

    <!-- This element is responsible to show the router content!!! -->
    <router-view />
  </div>
</template>

<script>
export default {
  data() {
    return {

    }
  }
}
</script>
```

## Libs

### vue-validate

https://www.npmjs.com/package/vee-validate

vee-validate is a plugin for Vue.js that allows you to validate input fields and display errors.

```cmd
npm install vee-validate --save
```

#### documentation

<https://baianat.github.io/vee-validate/>

## Animate.css

<https://daneden.github.io/animate.css/>

## vue-router

<https://router.vuejs.org/>

```cmd
npm install vue-router --save
```

## fonts-awesome

<https://fontawesome.com/>