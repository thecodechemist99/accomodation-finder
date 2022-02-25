<template>
  <form @submit.prevent="saveNotice" class="box">
    <fieldset>
      <label>Country*:</label>
      <input type="text" v-model="notice.country"/>
    </fieldset>
    <fieldset>
      <label>Location*:</label>
      <input type="text" v-model="notice.location"/>
    </fieldset>
    <fieldset>
    <label>Spaces*:</label>
      <input type="number" min="0" v-model="notice.spaces"/>
    </fieldset>
    <fieldset>
      <label>Start:</label>
      <input type="date" v-model="notice.start"/>
    </fieldset>
    <fieldset>
      <label>End:</label>
      <input type="date" v-model="notice.end"/>
    </fieldset>
    <fieldset>
      <label>Your Name*:</label>
      <input type="text" v-model="notice.name"/>
    </fieldset>
    <fieldset>
      <label>Contact Details*:</label>
      <input type="text" v-model="notice.contact"/>
    </fieldset>
    <fieldset>
      <label>Additional information:</label>
      <input type="text" v-model="notice.infos"/>
    </fieldset>
    <button>Save</button>
  </form>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'AddForm',
  setup(_, context) {
    const notice = ref({
      country: '',
      location: '',
      spaces: 0,
      start: '',
      end: '',
      name: '',
      contact: '',
      infos: '',
    });

    function saveNotice() {
      context.emit('saveNotice', notice.value);
    }

    return { notice, saveNotice };
  },
});
</script>

<style>
form {
  padding: 20px;

  display: flex;
  flex-direction: column;
  justify-content: left;

  border: solid #2c3e50;
}

fieldset {
  margin: 5px;
  padding: 0px;

  display: flex;
  flex-direction: column;

  text-align: left;

  border: none;
}

label {
  color: black;
}

input {
  margin: 5px 0px;
  padding: 5px;

  background: #eee;
  border-radius: 6px;
}

form > button {
  margin: 10px 0px;
}
</style>
