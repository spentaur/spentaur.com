<template>
  <div class="flex flex-col min-h-screen">
    <navbar />
    <div class="container w-full md:max-w-3xl flex-1 mx-auto pt-16 sm:pt-20">
      <nuxt />
    </div>
    <blog-footer />
  </div>
</template>

<script>
import Navbar from '~/components/Navbar'
import BlogFooter from '~/components/Footer'
export default {
  components: {
    Navbar,
    BlogFooter
  }
}
</script>
