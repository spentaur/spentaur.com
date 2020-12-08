<template>
  <div class="w-full">
    <div class="lg:flex">
      <div class="lg:w-1/3">
        <a href="https://listingwall.net">
          <img src="/lw.png" />
        </a>
      </div>
      <div class="lg:w-2/3 lg:pl-6">
        <div class="text-gray-900 text-2xl mb-2">
          <a href="https://listingwall.net" class="text-orange-500">
            ListingWall
          </a>
        </div>
        <p class="text-gray-700 text-base font-thin mb-3">
          ListingWall is a project I've been working on in my free time since
          November 2013. It started as and exercise to teach myself PHP and
          refine my CSS and JS skills, but has grown into something that I'm
          very passionate about.
        </p>
        <p class="text-gray-700 text-base font-thin">
          It's a website similar to Craigslist, where users can upload
          apartments for rent, houses for sale, job listings, etc. but with a
          few key changes that I think result in a much better experience.
        </p>
      </div>
    </div>
    <div class="mt-16 lg:flex">
      <div class="lg:w-1/3">
        <a href="https://post-here.com">
          <img src="/ph.png" />
        </a>
      </div>
      <div class="lg:w-2/3 lg:pl-6">
        <div class="text-gray-900 text-2xl mb-2">
          <a href="https://post-here.com" class="text-orange-500">
            Post Here
          </a>
        </div>
        <p class="text-gray-700 text-base font-thin">
          Post-Here.com uses a BERT classification model and ~4,000,000 posts
          mined from ~5,000 subreddits. The front end uses Nuxt and tailwind UI
          and is deployed as a static site to Cloudflare using Cloudflare
          workers. The model was converted to ONNX and uses Azure Functions and
          onnxruntime to run inferences. Please refer to the following repos and
          blog posts below for more information, and code examples.
        </p>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  auth: false,
  head() {
    return {
      title: 'Web Sites',
      meta: [
        {
          hid: `description`,
          name: 'description',
          content: 'A collection of my web sites.',
        },
      ],
    }
  },
}
</script>
