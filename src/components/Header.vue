<template>
  <header>
    <h1>Accomodation Finder</h1>
    <button @click="addNotice">Add</button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'Header',
  setup(_, context) {
    function addNotice() {
      context.emit('addNotice');
    }

    return { addNotice };
  },
});
</script>

<style>
header {
  padding: 10px 20px;

  display: flex;
  justify-content: space-between;
  align-items: center;

  background: #0066cc;
  box-shadow: 0px 5px 5px #333;
}

h1 {
  color: #ffcc00;
}

button {
  padding: 10px;

  font-size: 1.2em;
  font-weight: bold;
  color: #0066cc;

  border: none;
  border-radius: 10px;
  background: #ffcc00;
  box-shadow: 0px 2px 2px #333;
}
</style>
