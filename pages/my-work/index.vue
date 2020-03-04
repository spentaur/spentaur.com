<template>
  <div class="md:flex md:flex-row">
    <div class="overflow-hidden md:w-1/2 mx-3 mb-8 trans max-w-lg">
      <nuxt-link to="my-work/photography">
        <img
          class="w-full shadow md:shadow-none rounded md:rounded-none"
          src="/markie.jpg"
        />
      </nuxt-link>
      <div class="mt-3 text-center">
        <div class="font-bold text-lg mb-2">
          <nuxt-link to="my-work/photography" class="text-orange-500">
            Photogaphy
          </nuxt-link>
        </div>
      </div>
    </div>
    <div class="overflow-hidden md:w-1/2 mx-3 mb-8 trans max-w-lg">
      <nuxt-link to="my-work/web">
        <img
          class="w-full shadow md:shadow-none rounded md:rounded-none"
          src="/lw.png"
          alt="Preview of ListingWall.net"
        />
      </nuxt-link>
      <div class="mt-3 text-center">
        <div class="font-bold text-lg mb-2">
          <nuxt-link to="my-work/web" class="text-orange-500">
            Web Development
          </nuxt-link>
        </div>
      </div>
    </div>
    <!-- <div class="overflow-hidden md:w-1/2 mx-3 mb-8 trans max-w-lg">
      <nuxt-link to="my-work/data">
        <img
          class="w-full shadow md:shadow-none rounded md:rounded-none"
          src="img/lw.png"
          alt="Sunset in the mountains"
        />
      </nuxt-link>
      <div class="mt-3 text-center">
        <div class="font-bold text-lg mb-2">
          <nuxt-link to="my-work/data" class="text-orange-500">
            Data Science
          </nuxt-link>
        </div>
      </div>
    </div> -->
  </div>
</template>
<script>
export default {
  auth: false,
  head() {
    return {
      title: 'My Work',
      meta: [
        {
          hid: `description`,
          name: 'description',
          content: 'A collection of my work.'
        }
      ]
    }
  }
}
</script>
