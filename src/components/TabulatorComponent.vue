<template>
  <div
    ref="table"
    class="tabulator"
  />
</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Tabulator from 'tabulator-tables';

interface State {
  tabulatorInstance: Tabulator | null;
}

export default defineComponent({
  name: 'TabulatorComponent',
  props: {
    options: {
      type: Object as PropType<Tabulator.Options>,
      required: false,
    },
    modelValue: Object,
    data1: {
      type: Object,
      required: false,
    },   
  },
  data: (): State => {
    return { tabulatorInstance: null }
  },
  methods: {
    createTable(): void {
      this.tabulatorInstance = new Tabulator(
        (this.$refs.table as HTMLElement),
        this.options
      );
    }
  },
});
</script>