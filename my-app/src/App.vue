<template>
  <div id="app">
    <navbar></navbar>
    <menu-of-app @currentComponent = 'currentComponent'></menu-of-app>

    <component v-bind:is="currentComponentOfApp"></component>
  </div>
</template>

<script>
import Notes from './components/Notes.vue';
import Navbar from './components/Navbar-note';
import MenuOfApp from "./components/MenuOfApp";
import Library from "./components/Library";

export default {
    name: 'app',
    data: () => {
         return{
             currentComponentOfApp: 'notes'
         }
    },
    components: {
        Library,
        MenuOfApp,
        Notes,
        Navbar
    },
    methods: {
        currentComponent(data){
          this.currentComponentOfApp = data['currentTab'];
        }
    }
}
</script>

<style>

</style>
