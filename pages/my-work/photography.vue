<template>
  <div class="flex flex-row flex-wrap justify-center lg:mt-6">
    <img
      class="sm:w-56 sm:h-56 w-full h-full hover:w-auto object-cover"
      src="/photos/1.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover"
      src="/photos/2.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/3.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/4.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/5.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/6.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/7.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/8.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/9.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/10.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover"
      src="/photos/11.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover"
      src="/photos/12.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/13.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover object-top"
      src="/photos/14.jpg"
    />
    <img
      class="sm:w-56 sm:h-56 w-full h-full object-cover"
      src="/photos/15.jpg"
    />
  </div>
</template>
<style lang="postcss" scoped>
img {
  margin: 1px;
}
</style>
<script>
export default {
  auth: false,
  head() {
    return {
      title: 'Photography',
      meta: [
        {
          hid: `description`,
          name: 'description',
          content: 'A collection of my photography.'
        }
      ]
    }
  }
}
</script>
