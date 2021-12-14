<template>
  <main>
    <section class="w-full max-w-5xl mx-auto">
      <p v-if="$fetchState.pending">Loading....</p>
      <div
        v-else-if="$fetchState.error"
        class="bg-red-100 border border-red-400 text-red-700 px-4 py-3 rounded relative"
        role="alert"
      >
        <strong class="font-bold">Sorry!</strong>
        <span class="block sm:inline"
          >Something seriously bad happened. We are unable to getch the guest list, Please try again later.</span
        >
      </div>
      <ul v-else>
        <h1 class="title">Guest List</h1>
        <li v-for="(mountain, index) in mountains" :key="index">
          {{ mountain.title }}
        </li>
      </ul>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      mountains: [],
    }
  },
  async fetch() {
    this.mountains = await fetch('https://api.netlify.com/api/v1/forms/guestEntry/submissions').then((res) =>
      res.json()
    )
  },
}
</script>
