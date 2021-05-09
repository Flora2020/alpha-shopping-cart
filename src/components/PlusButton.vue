<template>
  <div class="bg">
    <div class="plus">+</div>
  </div>
</template>

<style>
.bg {
  position: relative;
  width: 26px;
  height: 27px;
  border-radius: 50%;
  background: #f0f0f5;
}

.bg:hover {
  cursor: pointer;
}

.plus {
  position: absolute;
  left: 6px;
  width: 100%;
  margin: 0 auto;
  line-height: 27px;
  font-size: 24px;
  color: #2a2a2a;
}
</style>