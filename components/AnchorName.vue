<template>
  <div class="anchor-name-container">
    <div class="tooltip tooltip-1">I'm an anchored tooltip.</div>
    <div class="tooltip tooltip-2">Me too!</div>
    <div class="el">Just Some Element</div>
  </div>
</template>

<style scoped>
.anchor-name-container {
  width: 20vw;
}

.container {
  display: flex;
  gap: 2rem;
}

.el {
  anchor-name: --my-anchor;
  background: orange;
  color: white;
  padding: 3rem;
  position: relative;
}

.tooltip {
  background: red;
  color: white;
  padding: 1rem;
  position: absolute;
  z-index: 1;
}

.tooltip-1 {
  bottom: anchor(--my-anchor top);
  left: anchor(--my-anchor center);
  transform: translate(-50%, -10px);
  &::after {
    content: "";
    width: 0;
    height: 0;
    border-top: 10px solid red;
    border-left: 10px solid transparent;
    border-right: 10px solid transparent;
    top: 100%;
    left: 50%;
    position: absolute;
  }
}

.tooltip-2 {
  top: anchor(--my-anchor center);
  left: anchor(--my-anchor right);
  transform: translate(0, -50%);
}

.anchor {
  background: var(--blue-4);
  text-align: center;
  font-weight: bold;
  border-radius: var(--radius-2);
  padding: var(--size-2);
  display: inline-block;
}

* {
  box-sizing: border-box;
}
</style>
