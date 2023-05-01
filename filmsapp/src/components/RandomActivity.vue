<template>
  <Activity
    class="center"
    v-if="activity"
    :activity="activity"
    :accessibility="accessibility"
    :type="type"
    :participants="participants"
    :price="price"
    :link="link"
    :key="key"
  />
  <button class="button-41 center" v-if="activity" @click="addActivity(activityData)">Add activity</button>
  <button class="button-40 center" @click="getRandomActivity">Get Random Activity</button>
</template>
<script lang="ts">
import axios from "axios";
import { Options, Vue } from 'vue-class-component';
import Activity from "./Activity.vue";

interface ActivityData {
  activity: string;
  accessibility: number;
  type: string;
  participants: number;
  price: number;
  link: string;
  key: string;
}

@Options({
    components: {
        Activity,
    },
})

export default class RandomActivity extends Vue {

  activityData: ActivityData = {
    activity: "",
    accessibility: 0,
    type: "",
    participants: 0,
    price: 0,
    link: "",
    key: "",
  };

  async getRandomActivity() {
    try {
      const response = await axios.get<ActivityData>('https://www.boredapi.com/api/activity');
      this.activityData = response.data;
    } catch (error) {
      console.log(error);
    }
  }

  addActivity(activityData: ActivityData) {
   this.$emit("addNewActivity", activityData);
  }

  get activity() {
    return this.activityData.activity;
  }

  get accessibility() {
    return this.activityData.accessibility;
  }

  get type() {
    return this.activityData.type;
  }

  get participants() {
    return this.activityData.participants;
  }

  get price() {
    return this.activityData.price;
  }

  get link() {
    return this.activityData.link;
  }

  get key() {
    return this.activityData.key;
  }
}
</script>




<style>

.button-40 {
  margin: 10px;
  background-color: #111827;
}

.button-40:hover {
  background-color: #374151;
}

.button-41 {
  margin: 10px;
  background-color: #2986CC;
}

.button-41:hover {
  background-color: #3E92D1;
}

.center{
  display: block;
  margin-left: auto;
  margin-right: auto;
}
</style>