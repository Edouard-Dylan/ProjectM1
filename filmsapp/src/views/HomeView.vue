<template>
  <MyActivities/>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import MyActivities from '@/components/MyActivities.vue';

@Options({
  components: {
    MyActivities,
  },
})
export default class HomeView extends Vue {
  activity = '';
  accessibility = 0;
  type = '';
  participants = 0;
  price = 0;
  link = '';
  key = '';
}
</script>
