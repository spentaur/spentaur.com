<template>
  <div class="flex flex-col min-h-screen">
    <div class="header fixed w-full">
      <div class="w-full bg-orange-500 p-2 lg:p-4 shadow">
        <div
          :class="{
            'height-2': !atTop,
          }"
          class="h-20 lg:h-24 trans lg:max-w-5xl flex mx-auto text-right"
        >
          <div class="trans" :class="{ 'slide-left': !atTop }">
            <nuxt-link to="/" exact>
              <img
                class="h-20 w-20 lg:w-48 lg:h-48 trans rounded-full border-8 border-orange-600 mr-2 lg:mr-4"
                src="/me.jpg"
                alt="Spencer Adams"
              />
            </nuxt-link>
          </div>
          <div class="flex-grow flex flex-col">
            <div
              :class="{ 'slide-up': !atTop }"
              class="text-2xl trans font-extrabold uppercase lg:text-4xl flex-grow text-orange-200"
            >
              Spencer<span class="text-orange-900">Adams</span>
            </div>
            <div
              class="text-sm lg:text-base font-semibold text-orange-200 content-end font-sans"
            >
              <nuxt-link
                to="/"
                class="px-1 lg:p-2 hover:bg-white hover:text-orange-500"
                exact
              >
                About Me
              </nuxt-link>
              <nuxt-link
                to="/my-work"
                class="px-1 lg:p-2 hover:bg-white hover:text-orange-500"
              >
                My Work
              </nuxt-link>
              <nuxt-link
                to="/blog"
                class="px-1 lg:p-2 hover:bg-white hover:text-orange-500"
              >
                Blog
              </nuxt-link>
              <nuxt-link
                to="/contact"
                class="px-1 lg:p-2 hover:bg-white hover:text-orange-500"
              >
                Contact
              </nuxt-link>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div
      class="container mt-32 lg:mt-40 mb-12 px-4 max-w-3xl mx-auto flex items-center flex-1 justify-center"
    >
      <nuxt />
    </div>
  </div>
</template>

<style lang="postcss" scoped>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

.nuxt-link-active {
  @apply text-orange-900;
}
</style>

<script>
export default {
  data() {
    return {
      atTop: true,
    }
  },
  created() {
    if (process.browser) {
      // eslint-disable-next-line nuxt/no-globals-in-created
      window.addEventListener('scroll', this.handleScroll)
    }
  },
  destroyed() {
    if (process.browser) {
      window.removeEventListener('scroll', this.handleScroll)
    }
  },
  methods: {
    handleScroll() {
      // Any code to be executed when the window is scrolled
      const scrollpos = window.scrollY
      if (scrollpos > 20) {
        this.atTop = false
      } else {
        this.atTop = true
      }
    },
  },
}
</script>
