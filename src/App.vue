<script setup>
import Intro from './components/IntroComponent.vue'
import Description from './components/DescriptionComponent.vue'
import Socials from './components/SocialsComponent.vue'
import Construction from './components/ConstructionComponent.vue'
import Canvas from './components/CanvasComponent.vue'
</script>

<template>
  <main>
    <div>
      <Intro />
      <Description />
    </div>
    <Socials />
    <Construction />
  </main>
  <Canvas />
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
