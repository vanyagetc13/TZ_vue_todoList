<template>
  <div class="card">
    <slot />
  </div>
</template>


<style>
.card {
  background: #FFFFFF;
  min-height: 20px;
  box-shadow: 0px 10px 25px rgba(29, 52, 54, 0.08);
  border-radius: 10px;
  padding: 20px;
  width: 100%;
}

.card h3 {
  color: #29A19C;
  margin-bottom: 10px;
}
</style>