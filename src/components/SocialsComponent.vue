<script setup>
import IconEmail from './icons/IconEmail.vue'
import IconGithub from './icons/IconGithub.vue'
import IconCodepen from './icons/IconCodepen.vue'
import IconLinkedin from './icons/IconLinkedin.vue'
</script>

<template>
  <div class="socials-wrapper">
    <p>Let's build your project.</p>
    <div class="socials">
      <a href="mailto:thomas.miller147@gmail.com" target="_blank" title="Contact by email"
        ><IconEmail
      /></a>
      <a href="https://github.com/Meuss" target="_blank" title="Github profile"><IconGithub /></a>
      <a href="https://codepen.io/Meuss/" target="_blank" title="Codepen profile"
        ><IconCodepen
      /></a>
      <a
        href="https://www.linkedin.com/in/thomas-miller-671589a3/"
        target="_blank"
        title="Linkedin profile"
      >
        <IconLinkedin
      /></a>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.socials {
  display: flex;
  align-items: center;
}
a {
  margin-right: 20px;
  width: 35px;
  padding: 5px;
  display: inline-flex;
  :deep(svg path) {
    fill: $text;
    transition: fill 0.2s ease-in-out;
  }
  &:hover {
    :deep(svg path) {
      fill: $accent;
    }
  }
}
p {
  margin-bottom: 15px;
  @include xs {
    margin-bottom: 5px;
  }
}
</style>
