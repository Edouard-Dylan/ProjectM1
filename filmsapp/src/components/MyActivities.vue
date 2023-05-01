<template>
  <div>
    <RandomActivity v-on:addNewActivity="addActivity"/>
    <h2>My Activities</h2>
    <ul class="cards-list">
      <li v-for="(activity, index) in activities" :key="index">
        <Activity :activity="activity.activity" :accessibility="activity.accessibility" :type="activity.type" :participants="activity.participants" :price="activity.price" :link="activity.link" :key="activity.key"/>
        <button class="remove" @click="removeActivity(index)">Remove</button>
      </li>
    </ul>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';
import Activity from "./Activity.vue";
import RandomActivity from '@/components/RandomActivity.vue';

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
    RandomActivity,
  }
})

export default class MyActivities extends Vue {
  activities: ActivityData[] = [];

  addActivity(activity: ActivityData){
    this.activities.push(activity);
  }

  removeActivity(index: number) {
    this.activities.splice(index, 1);
  }
}
</script>
<style>
*{
  font-family: nunito,roboto,proxima-nova,"proxima nova",sans-serif;
  padding: 0;
}
.remove{
  background-color: #F23535;
}

button {
  border: 1px solid transparent;
  border-radius: .75rem;
  box-sizing: border-box;
  color: #FFFFFF;
  cursor: pointer;
  flex: 0 0 auto;
  font-family: "Inter var",ui-sans-serif,system-ui,-apple-system,system-ui,"Segoe UI",Roboto,"Helvetica Neue",Arial,"Noto Sans",sans-serif,"Apple Color Emoji","Segoe UI Emoji","Segoe UI Symbol","Noto Color Emoji";
  font-size: 1.125rem;
  font-weight: 600;
  line-height: 1.5rem;
  padding: .75rem 1.2rem;
  text-align: center;
  text-decoration: none #6B7280 solid;
  text-decoration-thickness: auto;
  transition-duration: .2s;
  transition-property: background-color,border-color,color,fill,stroke;
  transition-timing-function: cubic-bezier(.4, 0, 0.2, 1);
  user-select: none;
  -webkit-user-select: none;
  touch-action: manipulation;
  width: auto;
}

.remove:hover {
  background-color: #F34949;
}

button:focus {
  box-shadow: none;
  outline: 2px solid transparent;
  outline-offset: 2px;
}

@media (min-width: 768px) {
  button {
    padding: .75rem 1.5rem;
  }
}

.cards-list {
  z-index: 0;
  width: 100%;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
  list-style: none;
}
</style>