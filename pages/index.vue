<template>
  <div
    style="width:100%;height:100vh;background-color: #00071c;"
    class="container super"
  >
    <canvas id="c"> </canvas>

    <div class="absolute z-10 w-full mx-auto ">
      <section
        class="flex px-6 md:px-32 pb-16 md:pt-32 flex-col justify-between  home"
      >
        <transition name="write" type="out-in">
          <div
            v-if="loaded"
            class="home__profile text-white flex flex-col justify-center h-full"
          >
            <p class="text-gray-600 md:text-lg pb-4">AYODOTUN AJALA</p>
            <h1 class="font-bold text-2xl md:text-4xl">
              Frontend Developer From Lagos, Nigeria
            </h1>
            <h1 class="font-bold text-2xl md:text-4xl">
              Bsc. Computer Engineering
            </h1>
          </div>
        </transition>

        <transition name="scroll">
          <div v-if="loaded" class="self-start flex items-center">
            <img class="h-10" src="@/assets/svgs/scroll.svg" alt="scroll" />
            <p class="text-sm text-gray-400 text-white pl-3">scroll</p>
          </div>
        </transition>
      </section>

      <section
        class="flex px-6 md:px-32 pb-16 md:pt-32 flex-col justify-between  home"
      >
        <div data-aos="fade-up">
          <h1>Hello Dev Community!</h1>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
class Star {
  constructor(radius, speed, width, xPos, yPos) {
    this.radius = radius
    this.speed = speed
    this.width = width
    this.xPos = xPos
    this.yPos = yPos
    this.opacity = 0.05 + Math.random() * 0.5
    this.color =
      ['rgb(23, 198, 61,', 'rgb(205, 99, 99,', 'rgb(195, 98, 186,'][
        Math.round(Math.random() * 3)
      ] +
      this.opacity +
      ')'

    this.counter = 0
    this.sign = Math.floor(Math.random() * 2) ? -1 : 1
  }

  update(ctx) {
    this.counter += this.sign * this.speed

    ctx.beginPath()
    ctx.arc(
      this.xPos + (this.counter / 100) * this.radius,
      this.yPos + this.counter / 100,
      this.width,
      0,
      Math.PI * 2,
      false
    )

    ctx.closePath()

    ctx.fillStyle = this.color
    ctx.fill()
  }
}

export default {
  data() {
    return {
      canvas: null,
      ctx: null,
      stars: [],
      loaded: false
    }
  },
  // created() {
  //   AOS.init()
  // },
  async mounted() {
    this.canvas = document.getElementById('c')
    this.ctx = this.canvas.getContext('2d')

    this.canvas.width = window.innerWidth
    this.canvas.height = window.outerHeight

    window.addEventListener('resize', this.windowResize)

    if (this.canvas && this.ctx) {
      await this.setupStars()
      this.loaded = true
    }
  },

  methods: {
    windowResize() {
      this.canvas.width = window.innerWidth
      this.canvas.height = window.innerHeight
    },
    drawAndUpdate() {
      this.ctx.clearRect(0, 0, this.canvas.width, this.canvas.height)

      this.ctx.fillStyle = '#00071C'
      this.ctx.fillRect(0, 0, this.canvas.width, this.canvas.height)

      for (let i = 0; i < this.stars.length; i++) {
        const myStar = this.stars[i]
        myStar.update(this.ctx)
      }
      window.requestAnimationFrame(this.drawAndUpdate)
    },

    setupStars() {
      let freq

      if (this.canvas.width < 800) {
        freq = 3000
      } else {
        freq = 5000
      }
      for (let i = 0; i < freq; i++) {
        const randomX = Math.round(-20 + Math.random() * this.canvas.width * 10)
        const randomY = Math.round(
          -20 + Math.random() * this.canvas.height * 10
        )
        const speed = 0.2 + Math.random() * 2
        const size = 0.2 + Math.random() * 10
        const radius = 5 + Math.random() * 10

        const star = new Star(radius, speed, size, randomX, randomY)
        this.stars.push(star)
      }
      this.drawAndUpdate()
    }
  }
}
</script>

<style lang="scss" scoped>
@keyframes write {
  0% {
    opacity: 0;
    width: 0;
  }
  75% {
    opacity: 1;
  }
  100% {
    opacity: 1;
    width: 100%;
  }
}

#c {
  position: absolute; /* absolute */
  top: 0;
  left: 0;
  width: 100%; /* 100% */
  height: 100vh; /* 100% */
}

.write- {
  &enter {
    animation: write 4s;
  }
  &enter-active,
  &leave-active {
    animation: write 4s;
  }
}

.scroll- {
  &enter {
    opacity: 0;
    transform: translateY(50px);
  }
  &enter-active,
  &leave-active {
    transition: all 0.3s 1s ease-out;
  }

  &leave-to {
    opacity: 1;
    transform: translate(0);
  }
}

.home {
  height: 100vh;

  &__profile {
    /* animation-name: write;
    animation-duration: 4s;
    animation-delay: 2s; */
    overflow: hidden;

    p,
    h1 {
      width: calc(75vw);
    }
  }
}
</style>
