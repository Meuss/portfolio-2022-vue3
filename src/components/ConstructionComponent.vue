<script setup></script>

<template>
  <div class="construction">portfolio coming soon<br /><span>I'm busy...</span></div>
</template>

<style lang="scss" scoped>
.construction {
  position: absolute;
  top: 0;
  right: 0;
  font-size: 18px;
  line-height: 20px;
  text-align: right;
  span {
    font-size: 14px;
  }
  @include sm {
    display: none;
  }
}
</style>
