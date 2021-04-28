<script lang="ts">
import { defineComponent } from 'vue';
import Tabulator from 'tabulator-tables';

export default defineComponent({
  name: 'TabulatorComponent',
  props: {
    options: {
      type: Tabulator.Options,
      required: false,
    },
    modelValue: Object,
    data: {
      type: Object,
      required: false,
    },
  },
});
</script>