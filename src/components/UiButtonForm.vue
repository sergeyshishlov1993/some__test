<template>
  <button class="button">
    <slot />
  </button>
</template>

<script setup></script>

<style lang="scss" scoped>
.button {
  margin-top: 15px;
  align-self: flex-end;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
}
</style>
