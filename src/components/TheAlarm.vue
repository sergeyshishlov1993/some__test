<template>
  <div class="alarm">
    <slot />
  </div>
</template>

<style lang="scss" scoped>
.alarm {
  margin-top: 15px;
  display: flex;
  justify-content: space-between;
  padding: 15px;
  border: 2px solid teal;
}
</style>
