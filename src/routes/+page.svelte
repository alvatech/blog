<script>
  import ArrowRightIcon from '$lib/components/ArrowRightIcon.svelte'
  import PostsList from '$lib/components/PostsList.svelte'
  import { name } from '$lib/info.js'

  /** @type {import('./$types').PageData} */
  export let data
</script>

<svelte:head>
  <title>{name}</title>
  <meta name="description" content="a tech blog" />
</svelte:head>

<div class="flex flex-col flex-grow gap-8 pb-16">
  <section class="w-full">
    <PostsList posts={data.posts} />
    <div class="flex items-center justify-between gap-4 mb-8 mt-4 sm:mt-8">
      <a href="/blogs" class="flex items-center gap-1 text-sm font-medium text-rose-500"
        >View All <ArrowRightIcon class="w-4 h-4" /></a
      >
    </div>
  </section>
</div>
