<template>
  <div class="intro">
    Hey<br />
    I’m Thomas<br />
    I build <span><br /><span id="web">web</span><span id="scramble">sites</span></span>
  </div>
</template>

<script setup>
import { onMounted } from '@vue/runtime-core'
import { gsap } from 'gsap'
import { ScrambleTextPlugin } from 'gsap/ScrambleTextPlugin'
import { GSDevTools } from 'gsap/GSDevTools'
gsap.registerPlugin(ScrambleTextPlugin, GSDevTools)

onMounted(() => {
  const randomChars = '#-$?!:é+-123456798abcdefhiklmnorstuvwxz'
  const master = gsap.timeline({ repeat: -1, paused: true })
  const words = [
    'apps',
    'shops',
    '&nbsp;projects',
    '&nbsp;animations',
    '&nbsp;UI/UX',
    '&nbsp;templates',
    '&nbsp;APIs',
    '&nbsp;design',
    // '&nbsp;with javascript',
    'sites'
  ]
  function scramble(word) {
    const tl = gsap.timeline()
    tl.to('#scramble', {
      scrambleText: { text: word, chars: randomChars, revealDelay: 0.3, speed: 1 }
    })
    return tl
  }
  words.forEach((word) => {
    master.add(scramble(word), '+=4')
  })
  master.play()
})
</script>

<style lang="scss" scoped>
.intro {
  font-family: 'Warownia', Avenir, sans-serif;
  font-size: 70px;
  line-height: 1.2;
  margin-bottom: 75px;
  word-spacing: 5px;
  > span > br {
    display: none;
  }
  @include sm {
    font-size: 50px;
  }
  @include xs {
    font-size: 40px;
    > span > br {
      display: block;
    }
  }
  span,
  :deep(span) {
    color: $accent;
  }
}
</style>
