<template>
  <div
    ref="table"
    class="tabulator"
  ></div>
</template>

<script lang="ts">
import { defineComponent, PropType, reactive,watch,ref } from 'vue';
import Tabulator from 'tabulator-tables';

interface Props {
  value?: string | number | boolean |any;
}

type NewType=null;

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
    const tableData = ref(props.modelValue)
    console.log('data phrase')
    console.log(optionsData)
    console.log(props.options)
    console.log(props.modelValue)
    const tabulatorInstance :Tabulator|null = new Tabulator(
        (this.$refs.table as HTMLElement),
        props.options
      );    
    return{
      optionsData,dog,tableData,tabulatorInstance //tabulatorInstance//,vm
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
  mounted(): void{
    this.createTable(this.tabulatorInstance)    
  },
  watch: {        
    optionsData(newOptionsData,oldOptionsData){
      console.log('trigger')
      //this.createTable(this.tabulatorInstance);
    },
    tableData:{
      deep:true,
      immediate:true,
      handler(tableData){
        console.log('table data was triggered');
        if(this.tabulatorInstance !== undefined){        
          //this.tabulatorInstance.setData(this.tableData);
        }
      }
    }
  },
  setup(props): void{
    watch(()=>tableData,(oldValue:any,newValue: any) => {
      console.log(
        "Watch props.selected function called with args:"
      );
      // Both props are undefined so its just a bare callback func to be run
    }, {deep: true, immediate: true});
    /**watch(tableData, (val: any, old: any) => {
    console.log("count updated to be ", val)
    });**/
 
  }, 
  methods: {    
    createTable(tabulatorInstance:Tabulator): void {
      console.log('1')
      console.log(this.$refs.table)
       tabulatorInstance = new Tabulator(
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


function tableData(tableData: any, arg1: (first: any, second: any) => void) {
  throw new Error('Function not implemented.');
}
</script>