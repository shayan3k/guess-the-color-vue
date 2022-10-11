<template>
  <div class="box" :style="{ backgroundColor: backgroundColor }"></div>
</template>

<script>
export default {
  name: "MainBox",
  props: {
    backgroundColor: String,
  },
};
</script>

<style scoped>
.box {
  width: 250px;
  height: 250px;
  border-radius: 5px;
  margin-bottom: 20px;
}
</style>
