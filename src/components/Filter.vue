<template>
  <section class='filters'>
    <p>Filters ...</p>
    <button @click="addFilter">Add Filter</button>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Filter',
  props: {

  },
  setup() {
    function addFilter() {
      return '';
    }

    return { addFilter };
  },
});
</script>

<style scoped>
.filters {
  padding: 10px;
  display: flex;
  flex-direction: row;
  justify-content: left;
}

button {
  margin: 5px;

  font-size: 1em;
  color: #ffcc00;

  background: #0066cc;
}
</style>
