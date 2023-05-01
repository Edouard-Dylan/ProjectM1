<template>
  <div class="card">
    <h2>Activity: {{ activity }}</h2>
    <p>Accessibility: {{ accessibility }}</p>
    <p>Type: {{ type }}</p>
    <p>Participants: {{ participants }}</p>
    <p>Price: {{ price }}</p>
    <p>Link: <a :href="link">{{ link }}</a></p>
    <p>Key: {{ key }}</p>
  </div>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component';

@Options({
    props: {
      activity: String,
      accessibility: Number,
      type: String,
      participants: Number,
      price: Number,
      link: String,
      key: String,
    }
})

export default class Activity extends Vue {
  activity!: string;
  accessibility!: number;
  type!: string;
  participants!: number;
  price!: number;
  link!: string;
  key!: string;
}
</script>
<style>

.card {
  max-width: 526px;
  min-height: 256px;
  padding: 20px;
  background-color: #fff;
  border-radius: 8px;
  box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
  border: 4mm ridge rgba(211, 220, 50, .6);
}

</style>