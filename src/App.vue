<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link>
  </div>
  <div id ="App">
    <VueTabulator
      v-model="data"
      :options="options"
    />
  </div>
  <router-view/>
</template>

<script lang="ts">
import { defineComponent, PropType, ref } from 'vue';
import VueTabulator from '@/components/TabulatorComponent.vue'

export default defineComponent({
  name: 'App',
  components: {
    VueTabulator
  },
  setup(){
    const columns = [{
      title: 'Name',
      field: 'name',
      sorter: 'string',
      width: 200,
      editor: true,
    },];
    const data = [{ name: 'Teste', age: 13 }];
    const options = null;
    const vm = this;
    /**
    get columns() {
          return this.columns;
        },
    set columns(value1: Array) {
          this.columns=value1:;
    }**/
    return {
      columns,data,options,vm
    }
  },
  methods: {
  get options(): PropType<Tabulator.Options> {
            
      return {
        columns: columns,
        rowClick(e: Event, row: Tabulator.RowComponent) {
          console.log('I clicked a row', vm, e, row);          
        },
      };
    }
  
  },
});
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
