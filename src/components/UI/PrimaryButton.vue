<template>
  <button class="button pointer">
    <slot />
  </button>
</template>

<script>
export default {};
</script>

<style scoped>
.button {
  font-family: inherit;
  padding: 10px 25px;
  background-color: #29A19C;
  color: #fafafa;
  border: none;
  font-weight: 600;
  font-size: 16px;
  border-radius: 8px;
  display: flex;
  align-items: center;
}
</style>