<script setup>
import { onMounted } from '@vue/runtime-core'
// code taken from an older codepen I made..
onMounted(() => {
  const canvas = document.getElementById('myCanvas')
  const c = canvas.getContext('2d')
  canvas.height = window.innerHeight
  canvas.width = window.innerWidth
  const canvasWidth = canvas.width
  const canvasHeight = canvas.height

  window.addEventListener('resize', () => {
    canvas.width = window.innerWidth
    canvas.height = window.innerHeight
  })

  function Circle(xCoordinate, yCoordinate, radius) {
    const randomNumber = Math.floor(Math.random() * 4)
    const randomTrueOrFalse = Math.floor(Math.random() * 2)

    this.xCoordinate = xCoordinate
    this.yCoordinate = yCoordinate
    this.radius = radius
    this.color = colorArray[randomNumber]

    if (randomTrueOrFalse === 1) {
      this.xVelocity = -Math.random() * 1
    } else {
      this.xVelocity = Math.random() * 1
    }

    if (randomTrueOrFalse === 1) {
      this.yVelocity = -Math.random() * 1
    } else {
      this.yVelocity = Math.random() * 1
    }

    this.update = function () {
      this.xCoordinate += this.xVelocity
      this.yCoordinate += this.yVelocity
      if (this.xCoordinate + this.radius > canvasWidth || this.xCoordinate - this.radius < 0) {
        this.xVelocity = -this.xVelocity
      }
      if (this.yCoordinate + this.radius > canvasHeight || this.yCoordinate - this.radius < 0) {
        this.yVelocity = -this.yVelocity
      }
      this.draw()
    }

    this.draw = function () {
      c.beginPath()
      c.arc(this.xCoordinate, this.yCoordinate, Math.abs(this.radius), 0, Math.PI * 2)
      c.fillStyle = this.color
      c.fill()
    }
  }

  const colorArray = ['rgba(0, 107, 184,.2)', 'rgba(91, 192, 190, .2)', 'rgba(0, 48, 82, .3)']
  const myCircle = new Circle(30, 80, 10)
  const circleArray = []
  const radiusPossibilities = [20, 40, 80]

  for (let i = 0; i < 5; i++) {
    const randomXCoordinate = Math.random() * canvasWidth
    const randomYCoordinate = Math.random() * canvasHeight
    const randomRadius = radiusPossibilities[Math.floor(Math.random() * radiusPossibilities.length)]
    circleArray.push(new Circle(randomXCoordinate, randomYCoordinate, randomRadius))
  }

  function updateAll() {
    c.clearRect(0, 0, canvasWidth, canvasHeight)
    myCircle.update()
    for (const value of circleArray) {
      value.update()
    }
    window.requestAnimationFrame(updateAll)
  }
  updateAll()
})
</script>

<template>
  <canvas id="myCanvas"></canvas>
</template>

<style lang="scss" scoped>
canvas {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  z-index: -1;
}
</style>
