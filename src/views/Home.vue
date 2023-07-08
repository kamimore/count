<template>
  <div>
    <Counter
      :year="2023"
      :month="7"
      :day="8"
      :hour="22"
      :minute="10"
      :second="10"
    />
  </div>
</template>

<script>
import Counter from "@/components/Counter.vue";
export default {
  components: {
    Counter,
  },
};
</script>
