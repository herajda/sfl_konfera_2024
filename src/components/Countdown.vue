<template>
  <div class="">
    <div class="grid grid-flow-col gap-5 text-center auto-cols-max justify-center">
      <div class="flex flex-col rounded-box text-neutral  bg-secondary flex-col p-2">
        <span class="font-bold countdown font-mono text-3xl">
          <span v-if="days > 99">{{ Math.floor(days / 100).toFixed(0) }}</span>
          <span :style="'--value:' + this.days % 100 + ';'"></span>
        </span>
        dní
      </div>
      <div class="flex flex-col rounded-box text-neutral  bg-secondary flex-col p-2">
        <span class="font-bold  countdown font-mono text-3xl">
          <span :style="'--value:' + this.hours % 100 + ';'"></span>
        </span>
        hod
      </div>
      <div class="flex flex-col rounded-box text-neutral  bg-secondary flex-col p-2">
        <span class="font-bold countdown font-mono text-3xl">
          <span :style="'--value:' + this.minutes % 100 + ';'"></span>
        </span>
        min
      </div>
      <div class="flex flex-col rounded-box text-neutral  bg-secondary flex-col p-2">
        <span class="font-bold countdown font-mono text-3xl">
          <span :style="'--value:' + this.seconds % 100 + ';'"></span>
        </span>
        sec
      </div>
    </div>
  </div>
</template>
<script>


export default {
  name: 'Countdown',
  data() {
    return {
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
      deadline: '2024-10-26T12:00:00'
    }
  },
  created() {
    this.getTimeRemaining()
  },
  methods: {
    getTimeRemaining() {
      setTimeout(() => {
        const total = new Date(this.deadline).getTime() - new Date().getTime();
        this.seconds = Math.floor((total / 1000) % 60);
        this.minutes = Math.floor((total / 1000 / 60) % 60);
        this.hours = Math.floor((total / (1000 * 60 * 60)) % 24);
        this.days = Math.floor(total / (1000 * 60 * 60 * 24));
        this.getTimeRemaining();
      }, 1000);


    }
  }

}
</script>