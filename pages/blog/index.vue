<template>
  <div class="px-3 sm:px-0 md:max-w-xl mx-auto">
    <results :blogs="blogs" />
  </div>
</template>

<script>
import Results from '~/components/Results'
export default {
  components: {
    Results,
  },
  layout: 'blog',
  data() {
    return {
      blogs: { data: [] },
    }
  },
  head() {
    return {
      title: 'Blog',
      meta: [
        {
          hid: `description`,
          name: 'description',
          content: 'These are some of my blogs. I hope you enjoy them.',
        },
      ],
    }
  },

  watchQuery: ['page'],
}
</script>
