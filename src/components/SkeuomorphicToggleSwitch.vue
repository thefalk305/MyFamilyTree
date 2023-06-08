<template>
  <div class="toggle-wrapper">
    <input class="toggle-checkbox" type="checkbox" />
    <svg class="toggle-icon off" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
      <path
        d="M16 8C16 12.4183 12.4183 16 8 16C3.58172 16 0 12.4183 0 8C0 3.58172 3.58172 0 8 0C12.4183 0 16 3.58172 16 8ZM2 8C2 11.3137 4.68629 14 8 14C11.3137 14 14 11.3137 14 8C14 4.68629 11.3137 2 8 2C4.68629 2 2 4.68629 2 8Z"
      />
    </svg>
    <div class="toggle-container">
      <div class="toggle-button"></div>
    </div>
    <svg class="toggle-icon on" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
      <path
        d="M16 8A8 8 0 1 1 0 8a8 8 0 1 1 16 0zM2 8a6 6 0 1 0 12 0A6 6 0 1 0 2 8zm10 0a4 4 0 1 1-8 0 4 4 0 1 1 8 0z"
      />
    </svg>
  </div>

  <div class="toggle-wrapper">
    <input class="toggle-checkbox" type="checkbox" checked />
    <svg class="toggle-icon off" viewBox="0 0 16 16" xmlns="http://www.w3.org/2000/svg">
      <path
        d="M16 8C16 12.4183 12.4183 16 8 16C3.58172 16 0 12.4183 0 8C0 3.58172 3.58172 0 8 0C12.4183 0 16 3.58172 16 8ZM2 8C2 11.3137 4.68629 14 8 14C11.3137 14 14 11.3137 14 8C14 4.68629 11.3137 2 8 2C4.68629 2 2 4.68629 2 8Z"
      />
    </svg>
    <div class="toggle-container">
      <div class="toggle-button"></div>
    </div>
    <svg class="toggle-icon on" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16">
      <path
        d="M16 8A8 8 0 1 1 0 8a8 8 0 1 1 16 0zM2 8a6 6 0 1 0 12 0A6 6 0 1 0 2 8zm10 0a4 4 0 1 1-8 0 4 4 0 1 1 8 0z"
      />
    </svg>
  </div>
</template>

<script>
// Design by kolpikov: https://dribbble.com/shots/14326768-Kn-bz-Skeuomorphic-UI-Sample-for-Figma
export default {};
</script>

<style scoped>
body {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 1em;
  min-height: 100vh;
  background-image: linear-gradient(45deg, #47b6d1, #90e0ec);
  font-size: 2em;
}

.toggle-wrapper {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  column-gap: 0.25em;
}

.toggle-icon {
  width: 0.5em;
  height: 0.5em;
  fill: #4c9bab;
  filter: drop-shadow(0 1px 1px rgb(255 255 255 / 0.4));
  transition: fill 0.4s;

  .toggle-checkbox:not(:checked) + &.off,
  .toggle-checkbox:checked ~ &.on {
    fill: #e0f9fc;
  }
}

.toggle-checkbox {
  -webkit-appearance: none;
  appearance: none;
  position: absolute;
  z-index: 1;
  border-radius: 3.125em;
  width: 4.05em;
  height: 100%;
  opacity: 0;
  cursor: pointer;
}

.toggle-container {
  position: relative;
  border-radius: 3.125em;
  width: 4.05em;
  height: 1.5em;
  background-image: repeating-conic-gradient(#0b66a0 0% 25%, #1093a8 0% 50%);
  background-size: 0.125em 0.125em;
  box-shadow: inset 0 0.125em 0.25em rgba(#000926, 0.6),
    inset -1.5em 0 0.0625em rgba(#000926, 0.5), inset 0.5em 0 0.5em rgba(#000926, 0.5),
    0 1px 1px rgb(255 255 255 / 0.4);
}

.toggle-button {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 0.0625em;
  left: 0.0625em;
  border-radius: inherit;
  width: 2.55em;
  height: calc(100% - 0.125em);
  background-image: linear-gradient(to right, #86e2fa, #125e79);
  box-shadow: 0 0.125em 0.25em rgb(0 0 0 / 0.6);
  transition: left 0.4s;

  .toggle-checkbox:checked ~ .toggle-container > & {
    left: 1.4375em;
  }

  &::before {
    content: "";
    position: absolute;
    top: inherit;
    border-radius: inherit;
    width: calc(100% - 0.375em);
    height: inherit;
    background-image: linear-gradient(to right, #0f73a8, #57cfe2, #b3f0ff);
  }

  &::after {
    content: "";
    position: absolute;
    width: 0.5em;
    height: 38%;
    background-image: repeating-linear-gradient(
      to right,
      #d2f2f6 0 0.0625em,
      #4ea0ae 0.0625em 0.125em,
      transparent 0.125em 0.1875em
    );
  }
}
</style>
