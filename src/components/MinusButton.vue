<template>
  <div class="bg">
    <div class="minus">–</div>
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

.minus {
  position: absolute;
  left: 7px;
  bottom: 3px;
  width: 100%;
  margin: 0 auto;
  line-height: 27px;
  font-size: 24px;
  font-weight: 500;
  color: #2a2a2a;
}
</style>