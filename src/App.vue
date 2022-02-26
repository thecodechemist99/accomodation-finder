<template>
  <Header @addNotice="addNotice" />
  <AddForm v-if="addingNotice" @saveNotice="saveNotice" />
  <div v-else>
    <FilterSection @addFilter="addFilter" @deleteFilter="deleteFilter" :filters="filters" />
    <NewFilter v-if="addingFilter" @saveFilter="saveFilter" :notices="notices" />
    <NoticeComp v-for="(notice, i) in showNotices" :key="i" :notice="showNotices[i]" />
  </div>
</template>

<script lang="ts">
import {
  computed,
  defineComponent,
  ref,
  Ref,
} from 'vue';
import Header from './components/Header.vue';
import AddForm from './components/AddForm.vue';
import NoticeComp from './components/Notice.vue';
import FilterSection from './components/FilterSection.vue';
import NewFilter from './components/NewFilter.vue';

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

export interface Filter {
  field: 'country' | 'location' | 'spaces' | 'start' | 'end' | 'name' | 'contact' | 'infos',
  value: string,
}

export default defineComponent({
  name: 'App',
  components: {
    Header,
    AddForm,
    NoticeComp,
    FilterSection,
    NewFilter,
  },
  setup() {
    const addingNotice = ref(false);
    const addingFilter = ref(false);

    const notices: Ref<Notice[]> = ref([]);
    const filters: Ref<Filter[]> = ref([]);

    const showNotices = computed(() => notices.value.filter(
      (notice: Notice) => filters.value.map(
        (filter: Filter) => notice[filter.field].toString() === filter.value,
      ).every((entry) => entry),
    ));

    function addNotice() {
      addingNotice.value = true;
    }

    function addFilter() {
      addingFilter.value = true;
    }

    function saveNotice(notice: Notice) {
      addingNotice.value = false;
      notices.value.push(notice);
    }

    function saveFilter(filter: Filter) {
      addingFilter.value = false;
      filters.value.push(filter);
      console.log(filters.value);
    }

    function deleteFilter(index: number) {
      filters.value.splice(index, 1);
    }

    return {
      addingNotice,
      addingFilter,
      notices,
      showNotices,
      filters,
      addNotice,
      addFilter,
      saveNotice,
      saveFilter,
      deleteFilter,
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
