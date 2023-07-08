<template>
  <div class="d-flex justify-content-center align-items-center">
    <div class="">
      <span>{{ displaydays }}</span>
      <span>:</span>
      <span>{{ displayhours }}</span>
      <span>:</span>
      <span>{{ displayminutes }}</span>
      <span>:</span>
      <span>{{ displayseconds }}</span>
      <span></span>
    </div>
  </div>
</template>

<script>
export default {
  props: ["year", "month", "day", "hour", "minute", "second"],
  data() {
    return {
      displaydays: "00",
      displayhours: "00",
      displayminutes: "00",
      displayseconds: "00",
    };
  },
  computed: {
    setRemaining() {
      let _seconds = 1000;
      let _minutes = 60 * _seconds;
      let _hours = 60 * _minutes;
      let _days = 24 * _hours;

      let interval = setInterval(() => {
        let now = new Date();
        let end = new Date(
          this.year,
          this.month - 1,
          this.day,
          this.hour,
          this.minute,
          this.second
        );
        console.log(end)
        console.log(end.getTime())
        console.log(now)
        console.log(now.getTime())
        let time = end.getTime() - now.getTime();
        console.log(time)
        if (time < 0) {
          clearInterval(interval);
          return 
        }

        let days = Math.floor(time / _days);
        let hours = Math.floor((time % _days) / _hours);
        let minutes = Math.floor((time % _hours) / _minutes);
        let seconds = Math.floor((time % _minutes) / _seconds);

        console.log(this.days)
        console.log(this.hours)
        console.log(this.minutes)
        console.log(this.seconds)

        console.log(this.displaydays)
        console.log(this.displayhours)
        console.log(this.displayminutes)
        console.log(this.displayseconds)

        this.displaydays = days < 10 ? `0${days}` : days;
        this.displayhours = hours < 10 ? `0${hours}` : hours;
        this.displayminutes = minutes < 10 ? `0${minutes}` : minutes;
        this.displayseconds = seconds < 10 ? `0${seconds}` : seconds;
      }, 1000);
    },
  },

  mounted() {
    this.setRemaining;
  },
};
</script>

<style lang="scss" scoped></style>
