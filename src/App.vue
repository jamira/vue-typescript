<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <ListItems :data="userInfo" @on-edit="getEditKey" @on-delete="getDeleteKey"/>
    <HelloWorld @add-user="getUserInfo" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import HelloWorld from './components/HelloWorld.vue'
import ListItems from '@/components/ListItems.vue'

@Component({
  components: {
    HelloWorld,
    ListItems
  }
})
export default class App extends Vue {
  userInfo: Array<object> = [];

  private getUserInfo (data: Record<string, any>): void {
    this.userInfo.push(data)
  }

  private getEditKey (key: number): void {
    console.log(`Edit key ${key}`)
  }

  private getDeleteKey (key: number): void {
    // this.userInfo.splice(key, 1) // javascript method delete
    this.$delete(this.userInfo, key) // vue method delete
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
</style>
