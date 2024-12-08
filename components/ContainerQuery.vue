<template>
  <div>
    <button @click="toggleWidth">Switch Container width</button>
    <div class="element-wrap" :class="{ fixedWidth: isFixedWidth }">
      <div class="element" v-for="i in 5" :key="i">
        <div class="fake-image"></div>
        <div>Element {{ i }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "ResponsiveContainer",
  data() {
    return {
      isFixedWidth: true,
    };
  },
  methods: {
    toggleWidth() {
      this.isFixedWidth = !this.isFixedWidth;
    },
  },
};
</script>

<style scoped>
button {
  background-color: bisque;
  color: brown;
  margin: 10px 0;
  padding: 5px;
  border-radius: 4px;
  cursor: pointer;
}

.fake-image {
  width: 100%;
  height: 35px;
  background-color: aqua;
}

.element-wrap {
  container-name: element;
  container-type: inline-size;
}

.fixedWidth {
  width: 299px;
}

.element {
  border: 1px solid aqua;
  margin: 1rem 0;
}

@container element (min-inline-size: 300px) {
  .element {
    display: flex;
    gap: 1rem;
    background-color: red;
    max-width: 500px;
  }
  .fake-image {
    width: 50px;
  }
}
</style>
