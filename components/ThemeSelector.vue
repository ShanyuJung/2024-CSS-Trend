<template>
  <div class="container">
    <select id="theme-selector">
      <option value="light" selected>Light</option>
      <option value="dark">Dark</option>
    </select>
    <p>
      Lorem Ipsum is simply dummy text of the printing and typesetting industry.
      Lorem Ipsum has been the industry's standard dummy text ever since the
      1500s, when an unknown printer took a galley of type and scrambled it to
      make a type specimen book. It has survived not only five centuries, but
      also the leap into electronic typesetting, remaining essentially
      unchanged. It was popularised in the 1960s with the release of Letraset
      sheets containing Lorem Ipsum passages, and more recently with desktop
      publishing software like Aldus PageMaker including versions of Lorem Ipsum
    </p>
  </div>
</template>

<style scoped>
.container {
  margin: 16px;
  --primary-color: rgb(82, 51, 238);
  --surface-color: #eee;
  --text-color: #1b1b1b;

  color: var(--text-color);
  background-color: var(--surface-color);
  border: 1px solid var(--primary-color);
}

.container:has(option[value="dark"]:checked) {
  --primary-color: #e43;
  --surface-color: #1b1b1b;
  --text-color: #eee;
}

option,
select {
  color: var(--text-color);
  background-color: var(--surface-color);
}
</style>
