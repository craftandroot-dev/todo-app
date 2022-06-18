<template>
  <div class="hello">
    <p>
      My first to do app project with vue cli, record your daily, weekly,
      monthly or yearly plans and realize your plans.
    </p>
    <h2>Technologies : SCSS, Router, Vuex, Babel</h2>
  </div>
</template>

<script>
import "@/assets/tailwind.css";
export default {
  name: "HelloWorld",
  props: {
    msg: String,
  },
};
</script>

<style scoped lang="scss">

</style>
