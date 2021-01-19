<template>
  <nav
    id="header"
    :class="{ 'navbar-white': whiteNav }"
    class="fixed w-full top-0 trans z-10"
  >
    <div
      class="w-full md:max-w-5xl mx-auto flex flex-wrap items-center justify-between mt-0 py-3"
    >
      <div class="pl-4">
        <nuxt-link
          to="/"
          class="navbar-brand text-white bg-orange-500 border-2 border-orange-500 no-underline font-bold font-serif px-1 py-1; block md:text-xl hover:no-underline hover:text-orange-500 hover:bg-transparent"
        >
          spentaur.
        </nuxt-link>
      </div>
      <div class="block lg:hidden pr-4">
        <button
          class="flex items-center text-gray-500 hover:text-gray-700"
          @click="menuHidden = !menuHidden"
        >
          <svg
            class="fill-current h-5 w-5"
            viewBox="0 0 20 20"
            xmlns="http://www.w3.org/2000/svg"
          >
            <title>Menu</title>
            <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z" />
          </svg>
        </button>
      </div>
      <div
        id="nav-content"
        :class="{ hidden: menuHidden }"
        class="w-full lg:flex font-semibold lg:items-center lg:w-auto lg:block mt-2 lg:mt-0 bg-white md:bg-transparent"
      >
        <ul
          class="list-reset m-0 p-0 list-inside lg:flex justify-end items-center"
        >
          <li>
            <nuxt-link
              to="/"
              class="inline-block hover:bg-orange-500 hover:text-orange-100 text-gray-600 no-underline hover:text-gray-900 hover:text-underline py-1 px-3"
              exact
            >
              About Me
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/my-work"
              class="inline-block hover:bg-orange-500 hover:text-orange-100 text-gray-600 no-underline hover:text-gray-900 hover:text-underline py-1 px-3"
            >
              My Work
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/blog"
              class="inline-block hover:bg-orange-500 hover:text-orange-100 text-gray-600 no-underline hover:text-gray-900 hover:text-underline py-1 px-3"
            >
              Blog
            </nuxt-link>
          </li>
          <li>
            <nuxt-link
              to="/contact"
              class="inline-block hover:bg-orange-500 hover:text-orange-100 text-gray-600 no-underline hover:text-gray-900 hover:text-underline py-1 px-3"
            >
              Contact
            </nuxt-link>
          </li>
        </ul>
      </div>
    </div>
    <vue-scroll-progress-bar
      v-if="scrollProgress"
      height=".1rem"
      :container-class="{ 'progress-bar-container--container': false }"
      class="scroll-progress-bar-not-fixed"
      background-color="linear-gradient(to right, #ed8936, #f6ad55)"
    />
  </nav>
</template>

<script>
export default {
  data() {
    return {
      whiteNav: false,
      menuHidden: true,
      atTop: true,
      hasJs: false,
      scrollProgress: false,
      search: '',
    }
  },
  watch: {
    menuHidden(oldVal, newVal) {
      if (newVal === true) {
        this.whiteNav = true
      } else if (this.atTop === true) {
        this.whiteNav = false
      }
    },
    $route(to, from) {
      this.menuHidden = true
      if ((to.name === 'blog-slug') | (to.name === 'blog-slug-edit')) {
        setTimeout(
          function () {
            this.scrollProgress = true
          }.bind(this),
          300
        )
      } else {
        this.scrollProgress = false
      }
    },
  },
  created() {
    if (process.browser) {
      // eslint-disable-next-line nuxt/no-globals-in-created
      window.addEventListener('scroll', this.handleScroll)
    }
    if (
      (this.$route.name === 'blog-slug') |
      (this.$route.name === 'blog-slug-edit')
    ) {
      this.scrollProgress = true
    } else {
      this.scrollProgress = false
    }
  },
  destroyed() {
    if (process.browser) {
      window.removeEventListener('scroll', this.handleScroll)
    }
  },
  methods: {
    handleScroll(event) {
      // Any code to be executed when the window is scrolled
      const scrollpos = window.scrollY
      if (scrollpos > 10) {
        this.whiteNav = true
        this.atTop = false
      } else if (this.menuHidden === false) {
        this.whiteNav = true
        this.atTop = true
      } else {
        this.whiteNav = false
        this.atTop = true
      }
    },
    submitSearch() {
      this.$router.push({ path: '/blog/search', query: { s: this.search } })
    },
  },
}
</script>

<style lang="postcss" scoped>
.navbar-white {
  @apply shadow bg-white;
}

.search-input {
  @apply bg-white border border-gray-300 rounded-lg ml-5 py-2 px-4 block w-full appearance-none leading-normal;
}

.nuxt-link-active:not(.navbar-brand) {
  @apply text-orange-500;
}
.nuxt-link-active:hover:not(.navbar-brand) {
  @apply text-orange-100;
}

.scroll-progress-bar-not-fixed {
  width: 100%;
  top: 0;
  left: 0;
}
</style>
