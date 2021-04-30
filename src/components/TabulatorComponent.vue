<template>
  <div
    ref="table"
    class="tabulator"
  ></div>
</template>

<script lang="ts">
import { defineComponent, PropType, reactive,watch,ref } from 'vue';
import Tabulator from 'tabulator-tables';

export default defineComponent({
  name: 'TabulatorComponent',
  props: {
    options: {
      type: Object ,
      required: false,
    },
    modelValue: Object,
    data1: {
      type: Object,
      required: false,
    },   
  }, 
  data(props) {
    //console.log('test')
    //const tabulatorInstance :Tabulator|null =this.createTable();
    /**
     * const tabulatorInstance :Tabulator|null =new Tabulator(
        (this.$refs.table as HTMLElement),
        props.options
      );
     * 
     */
    const dog='dog'
    const optionsData = ref(props.options)
    console.log('data phrase')
    console.log(optionsData)
    console.log(props.options)
    console.log(props.modelValue)
    return{
      optionsData,dog //tabulatorInstance//,vm
    }
    
  },/** 
  mounted(){    
    //const tabulatorInstance :Tabulator|null =this.createTable();
     console.log(this.options)
     console.log(this.$refs.table)
    const tabulatorInstance :Tabulator|null =new Tabulator(
        (this.$refs.table as HTMLElement),
        this.options
      );
    console.log('test')
    return{
      tabulatorInstance
    }
  },**/
  beforeCreate(): void{
    console.log('before create phrase')
    //const optionsData1 = ref(this.options)
    console.log(this.optionsData)   
    //watch(optionsData1, (optionsData1, prevoptionsData1): void => {   
    //  console.log('trigger')
    //  this.createTable();
    //})
    
  },
  mounted(){
    this.createTable()
  },
  watch: {
    optionsData(newOptionsData,oldOptionsData){
      console.log('trigger')
      this.createTable();
    }
  },
  methods: {    
    createTable(){
      console.log('1')
      console.log(this.$refs.table)
      const tabulatorInstance = new Tabulator(
        (this.$refs.table as HTMLElement),
        this.optionsData
      );
      console.log(this.options)
      console.log('2')
    }
  },
  
  /**watch:{
    'props.options'(){
                console.log('testaaa')
            }
  }**/
  
});

</script>