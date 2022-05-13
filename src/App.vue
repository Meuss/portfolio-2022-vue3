<script setup>
import Intro from './components/IntroComponent.vue'
import Description from './components/DescriptionComponent.vue'
import Socials from './components/SocialsComponent.vue'
</script>

<template>
  <main>
    <div>
      <Intro />
      <Description />
    </div>
    <Socials />
  </main>
</template>

<style lang="scss">
@import './assets/scss/base.scss';
main {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: space-between;
  height: 100%;
}
</style>
