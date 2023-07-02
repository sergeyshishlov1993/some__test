<template>
  <div class="post">
    <slot />
  </div>
</template>

<script setup></script>

<style lang="scss" scoped>
.post {
  display: flex;
  justify-content: space-between;
  padding: 15px;
  border: 2px solid teal;
  margin-top: 15px;
}
</style>
