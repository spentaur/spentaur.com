<template>
  <div class="w-full trans max-w-lg">
    <div class="mx-auto flex flex-col ">
      <span
        class="text-4xl text-gray-700 leading-none font-hairline mb-12 text-center"
      >
        <h1 v-if="error.statusCode === 404">Page not found</h1>
        <h1 v-else>An error occurred</h1>
      </span>
    </div>
  </div>
</template>

<script>
export default {
  // eslint-disable-next-line vue/require-prop-types
  props: ['error'],
  head() {
    return {
      title: 'Error'
    }
  },
  layout: 'default' // you can set a custom layout for the error page
}
</script>
