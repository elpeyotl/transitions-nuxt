<template>
  <section class="container">
    <div>
    <app-logo/>
      <h1 class="title">
        <span class="st">animations</span> <span class="st">Page2</span>
      </h1>
      <h2 class="subtitle">
        Nuxt.js project
      </h2>
      <div class="links">
       <nuxt-link class="button--green" to="/">Home</nuxt-link>
      </div>
    </div>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue'
import TimeLineMax from 'gsap'

export default {
  components: {
    AppLogo
  },
    transition: {
    mode: 'out-in',
    css: false,
        enter (el, done) {
            console.log('enter to page2')
            let tl = new TimelineMax({ onComplete: done })
            tl.staggerFromTo(
                '.st', 1,
                { y: '-20%', opacity:0},
                {y: '0%', opacity:1, ease: Back.easeOut.config(3.7)},0.2
            )
            tl.from('.subtitle',1,{x:'-500', opacity:0})


        },
        leave (el ,done) {
            let tl = new TimelineMax({ onComplete: done })
            tl.to('.subtitle',1,{x:'500', opacity:0})
            tl.staggerTo(
                '.st', 1,
                { y: '-20%', opacity:0},0.2
            )
        }
    }

}
</script>

<style>
.st {
    display: block;
}
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: "Quicksand", "Source Sans Pro", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; /* 1 */
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

