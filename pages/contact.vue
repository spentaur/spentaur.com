<template>
  <div>
    <transition name="fade" mode="out-in">
      <div v-if="loading & !success" class="opacity-50 lds-heart">
        <div></div>
      </div>
      <form
        v-else-if="!loading & !success"
        id="app"
        class="w-full max-w-lg"
        @submit.prevent="submit"
      >
        <div class="flex flex-wrap mx-3 mb-6">
          <div class="w-full px-3 my-6">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="grid-first-name"
            >
              Name
            </label>
            <input
              id="grid-first-name"
              v-model="form.name"
              :class="{ error: errors.name }"
              class="appearance-none block w-full bg-gray-300 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              type="text"
              placeholder="Jean-Luc Picard"
            />
            <!-- <p class="text-red-500 text-xs italic">
          Please fill out this field.
        </p> -->
          </div>
          <div class="w-full px-3 mb-6">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="grid-last-name"
            >
              Email
            </label>
            <input
              id="grid-last-name"
              v-model="form.email"
              :class="{ error: errors.email }"
              class="appearance-none block w-full bg-gray-300 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              type="email"
              placeholder="picard@starfleet.com"
            />
          </div>
          <div class="w-full px-3 mb-6">
            <label
              class="block uppercase tracking-wide text-gray-700 text-xs font-bold mb-2"
              for="grid-last-name"
            >
              Message
            </label>
            <textarea
              v-model="form.message"
              :class="{ error: errors.message }"
              class="appearance-none block h-64 w-full bg-gray-300 text-gray-700 border border-gray-200 rounded py-3 px-4 leading-tight focus:outline-none focus:bg-white focus:border-gray-500"
              placeholder="Captain's Log..."
            ></textarea>
          </div>
          <div class="w-full text-right px-3">
            <button
              class="bg-gray-300 hover:bg-transparent text-gray-700 font-semibold hover:text-gray-900 py-2 px-4 border border-transparent  hover:border-gray-500 rounded"
            >
              Submit
            </button>
          </div>
        </div>
      </form>
      <div
        v-else-if="success & !loading"
        class="text-2xl font-serif text-gray-700"
      >
        <p>
          Thanks for reaching out.
        </p>
        <p>I'll get back to you as soon as possible.</p>
      </div>
    </transition>
  </div>
</template>
<script>
export default {
  auth: false,
  data() {
    return {
      form: {
        name: '',
        email: '',
        message: ''
      },
      errors: {},
      loading: false,
      success: false
    }
  },
  watch: {
    // whenever question changes, this function will run
    form: {
      handler() {
        this.clearErrors()
      },
      deep: true
    }
  },
  methods: {
    checkForErrors() {
      if (!this.form.name) {
        this.$set(this.errors, 'name', true)
      }
      if (!this.form.email) {
        this.$set(this.errors, 'email', true)
      }
      if (!this.form.message) {
        this.$set(this.errors, 'message', true)
      }
    },
    clearErrors() {
      if (this.form.name) {
        this.$delete(this.errors, 'name')
      }
      if (this.form.email) {
        this.$delete(this.errors, 'email')
      }
      if (this.form.message) {
        this.$delete(this.errors, 'message')
      }
    },
    async submit() {
      this.checkForErrors()
      if (
        Object.entries(this.errors).length === 0 &&
        this.errors.constructor === Object
      ) {
        this.loading = true
        const resp = await this.$axios.$post(
          'https://formspree.io/xnqvagke',
          this.form
        )
        this.loading = false
        if (resp.ok) {
          this.success = true
        }
      }
    }
  },
  head() {
    return {
      title: 'Contact',
      meta: [
        {
          hid: `description`,
          name: 'description',
          content:
            'Please fill out this form, and I will get back to you as soon as possible.'
        }
      ]
    }
  }
}
</script>

<style lang="postcss" scoped>
.error {
  @apply border border-red-500;
}
</style>
