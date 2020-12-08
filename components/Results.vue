<template>
  <div v-if="blogs.data.length">
    <div v-for="blog in blogs.data" :key="blog.title" class="w-full flex mb-6">
      <div
        class="sm:p-4 flex-grow flex flex-col justify-between leading-normal"
      >
        <div class="h-full flex flex-col">
          <div class="">
            <nuxt-link
              class="text-sm text-gray-500 uppercase font-light hover:underline"
              :to="{ path: '/blog/search', query: { s: blog.category } }"
            >
              {{ blog.category }}
            </nuxt-link>
            <nuxt-link :to="'/blog/' + blog.slug">
              <div
                class="leading-tight text-gray-900 font-semibold sm:font-bold text-base sm:text-xl overflow-hidden sm:h-auto sm:overflow-auto mb-1"
              >
                {{ blog.title }}
              </div>
            </nuxt-link>
          </div>
          <div class="text-sm text-gray-500 uppercase font-light">
            {{ format_date(blog.updated_at) }}
          </div>
        </div>
      </div>
      <nuxt-link
        v-if="blog.featuredImgUrl"
        :style="'background-image: url(' + blog.featuredImgUrl + ')'"
        class="block mb-0 h-24 border border-gray-200 rounded w-24 sm:h-32 sm:w-32 flex-none bg-cover bg-center text-center overflow-hidden"
        :to="'/blog/' + blog.slug"
      />
    </div>
    <div
      v-if="blogs.next_page_url || blogs.prev_page_url"
      class="pt-4 pb-12 text-center"
    >
      <div class="inline-flex">
        <nuxt-link
          v-if="blogs.prev_page_url"
          :to="{
            path: $route.path,
            query: { s: $route.query.s, page: blogs.current_page - 1 },
          }"
          :class="{ 'rounded-r': !blogs.next_page_url }"
          class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded-l"
        >
          Prev
        </nuxt-link>
        <nuxt-link
          v-if="blogs.next_page_url"
          :to="{
            path: $route.path,
            query: { s: $route.query.s, page: blogs.current_page + 1 },
          }"
          :class="{ 'rounded-l': !blogs.prev_page_url }"
          class="bg-gray-300 hover:bg-gray-400 text-gray-800 font-bold py-2 px-4 rounded-r"
        >
          Next
        </nuxt-link>
      </div>
    </div>
  </div>
  <div v-else>
    <p class="text-center font-serif text-xl">
      No blogs yet, watch this instead.
    </p>
    <div class="youtube mt-8">
      <iframe
        src="https://www.youtube.com/embed/LTseTg48568"
        allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture"
        allowfullscreen="true"
        frameborder="0"
      ></iframe>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    blogs: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  methods: {
    format_date(date) {
      const months = [
        'JAN',
        'FEB',
        'MAR',
        'APR',
        'MAY',
        'JUN',
        'JUL',
        'AUG',
        'SEP',
        'OCT',
        'NOV',
        'DEC',
      ]
      const jsdate = new Date(date.replace(/-/g, '/'))
      const format =
        months[jsdate.getMonth()] +
        ' ' +
        jsdate.getDate() +
        ', ' +
        jsdate.getFullYear()
      return format
    },
  },
}
</script>
