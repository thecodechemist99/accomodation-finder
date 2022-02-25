<template>
  <article class="box">
    <div class="column">
      <div class="entry">
        <img src="../assets/passport.png" alt="Country" />
        <p>{{ notice.country }}</p>
      </div>
      <div class="entry">
        <img src="../assets/city.png" alt="Location" />
        <p>{{ notice.location }}</p>
      </div>
      <div class="entry">
        <img src="../assets/bed.png" alt="Spaces" />
        <p>{{ notice.spaces }}</p>
      </div>
      <div class="entry">
        <img src="../assets/calendar.png" alt="Duration" />
        <p>{{ notice.start }}<br />&ndash;<br/>{{ notice.end }}</p>
      </div>
      <div class="entry">
        <img src="../assets/information.png" alt="Additional Information" />
        <p>{{ notice.infos }}</p>
      </div>
    </div>
    <div class="column">
      <div class="entry">
        <img src="../assets/person_2.png" alt="Name" />
        <p>{{ notice.name }}</p>
      </div>
      <div class="entry">
        <img src="../assets/contact.png" alt="Contact Information" />
        <p>{{ notice.contact }}</p>
      </div>
    </div>
  </article>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
// import { Notice } from '../App.vue'

export default defineComponent({
  name: 'NoticeComp',
  props: {
    key: Number,
    notice: Object,
  },
});
</script>

<style scoped>
.entry {
  display: flex;

  flex-direction: row;
  justify-content: left;
  align-items: center;
}

.box {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
}

.column {
  min-width: 150px;
}

img {
  height: 35px;
  margin: 5px 15px 5px 5px;
}
</style>
