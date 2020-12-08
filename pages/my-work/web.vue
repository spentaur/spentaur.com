<template>
  <div>
    <div class="max-w-sm w-full lg:max-w-full lg:flex">
      <div class="flex">
        <a href="https://listingwall.net">
          <img src="/lw.png" />
        </a>
      </div>
      <div class="px-4 mt-4 lg:mt-0 flex flex-col leading-normal">
        <div>
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
