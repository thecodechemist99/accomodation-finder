<template>
  <Header @addNotice="addNotice" />
  <AddForm v-if="adding" @saveNotice="saveNotice" />
  <div v-else>
    <Filter />
    <NoticeComp v-for="(notice, i) in notices" :key="i" :notice="notices[i]" />
  </div>
</template>

<script lang="ts">
import {
  defineComponent,
  ref,
  Ref,
  toRaw,
} from 'vue';
import Header from './components/Header.vue';
import AddForm from './components/AddForm.vue';
import NoticeComp from './components/Notice.vue';
import Filter from './components/Filter.vue';

export interface Notice {
  country: string,
  location: string,
  spaces: number,
  start: string,
  end: string,
  name: string,
  contact: string,
  infos: string,
}

export default defineComponent({
  name: 'App',
  components: {
    Header,
    AddForm,
    NoticeComp,
    Filter,
  },
  setup() {
    const adding = ref(false);
    const notices: Ref<Notice[]> = ref([]);

    function addNotice() {
      adding.value = true;
    }

    function saveNotice(notice: Notice) {
      adding.value = false;
      notices.value.push(notice);
      console.log(notices.value);
    }

    return {
      adding,
      notices,
      addNotice,
      saveNotice,
    };
  },
});
</script>

<style>
body {
  margin: 0px;

  background: #ffcc00;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0px;
}

.box {
  margin: 10px;
  padding: 10px;

  border: none;
  border-radius: 25px;

  background: #0066cc;
  box-shadow: 0px 4px 4px #333;
}
</style>
