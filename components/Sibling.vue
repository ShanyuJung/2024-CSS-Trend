<template>
  <div>
    <div>我是前一個元素</div>
    <p>我是當前元素</p>
  </div>
</template>

<style scoped>
div:has(+ p) {
  color: red;
}

div + p {
  font-size: 20px;
}
</style>
