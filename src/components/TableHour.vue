<script setup lang="ts">
import { ref, watch } from 'vue';

const start = ref('00:00:00')
const stop = ref('00:00:00')
const total = ref('00:00:00')
const pause = ref('00:00:00')

const items = ref([
  {
    day: 'Monday',
    start: '',
    stop: '',
    pause: '',
    total: '',
  },
  {
    day: 'Tuesday',
    start: '',
    stop: '',
    pause: '',
    total: '',
  },
  {
    day: 'Wednesday',
    start: '',
    stop: '',
    pause: '',
    total: '',
  },
  {
    day: 'Thursday',
    start: '',
    stop: '',
    pause: '',
    total: '',
  },
  {
    day: 'Friday',
    start: '',
    stop: '',
    pause: '',
    total: '',
  },
  {
    day: 'Saturday',
    start: '',
    stop: '',
    pause: '',
    total: '',
  },
  {
    day: 'Sunday ',
    start: '',
    stop: '',
    pause: '',
    total: '',
  },
])

function calculateTotalHours(times: [string, string, string]) {
  let totalMinutes = 0;

  times.forEach(time => {
    const [hours, minutes] = time.split(':').map(Number);
    totalMinutes += (hours * 60) + minutes;
  });

  const totalHours = Math.floor(totalMinutes / 60);
  const remainingMinutes = totalMinutes % 60;

  console.log(`${totalHours}:${remainingMinutes.toString().padStart(2, '0')}`);
  
  return `${totalHours}:${remainingMinutes.toString().padStart(2, '0')}`;
}

watch(start,(changed)=>{
  console.log(changed, start);
  
})
</script>

<template>
  <div>
    <v-data-table :items="items" :hide-default-footer="true">      
      <template v-slot:item.start="props">
        <v-text-field label="Starting hour" :model-value="start" suffix="AM" type="time"></v-text-field>
      </template>

      <template v-slot:item.stop="props">
        <v-text-field label="Stoping hour" :model-value="stop" suffix="AM" type="time"></v-text-field>
      </template>

      <template v-slot:item.pause="props">
        <v-text-field label="Pause hour" :model-value="pause" suffix="AM" type="time"></v-text-field>
      </template>

      <template v-slot:item.total="props">
        <v-text-field label="Total hour" :model-value="total" suffix="AM" type="time"></v-text-field>
      </template>
    </v-data-table>
  </div>
</template>

<style scoped></style>
