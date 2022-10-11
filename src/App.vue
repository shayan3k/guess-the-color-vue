<template>
  <div class="container">
    <MainBox :background-color="backgroundColor" />

    <div>
      <button
        v-for="(item, index) in colors"
        :key="index"
        class="btn"
        @click="(e) => clickAction(item, e)"
      >
        {{ item }}
      </button>
    </div>
  </div>
</template>

<script>
import MainBox from "./components/MainBox.vue";

export default {
  name: "Index",
  components: {
    MainBox,
  },
  data() {
    return {
      colors: ["", "", ""],
      backgroundColor: "#efefef",
    };
  },
  mounted() {
    // add the color to the button
    this.colorGenerator();
  },
  methods: {
    colorGenerator() {
      // generate three random colors
      // 0 - 16777215
      const newColors = this.colors.map((item, index) => {
        return "#" + Math.trunc(Math.random() * 16777215).toString(16);
      });

      // store the three colors inside the state
      this.colors = [...newColors];

      // assign one of thoes colors to the background color
      const randomEl = Math.floor(Math.random() * (2 - 0 + 1) + 0);
      // setBackground_color(newColors[randomEl]);

      this.backgroundColor = newColors[randomEl];

      // reset all button classes
      document.querySelectorAll(".btn").forEach((item) => {
        item.classList.remove("btn-danger");
        item.classList.remove("btn-success");
      });
    },
    clickAction(color, e) {
      if (color == this.backgroundColor) {
        // add the color to the button
        e.target.classList.toggle("btn-success");

        // reset the background color
        this.colorGenerator();
      } else {
        // add the color to the button
        e.target.classList.toggle("btn-danger");
      }
    },
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.btn {
  margin-left: 5px;
  margin-right: 5px;
}
.btn-danger {
  background-color: rgb(190, 34, 34);
  color: white;
  outline: rgb(190, 34, 34);
}
.btn-success {
  background-color: rgb(34, 190, 86);
  color: white;
  outline: rgb(34, 190, 86);
}
</style>
