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
    this.mountains = await fetch(
      'https://api.netlify.com/api/v1/sites/e9b463c3-3389-4787-9d0e-a57b34fd10f4/forms/61b77c04c4895f0007bf9fcd/submissions?state=ham&page=1&per_page=20',
      {
        headers: {
          accept: '*/*',
          'accept-language': 'en-US,en;q=0.9',
          authorization: 'Bearer tO_M-Vp-V7tbtwxEnHXH4vOTHozUAaebSrxm90PtfrQ',
          'content-type': 'application/json',
          'if-none-match': 'W/"1ce6bb9be42b0b771e03365209be3f26"',
          'sec-ch-ua': '"Google Chrome";v="95", "Chromium";v="95", ";Not A Brand";v="99"',
          'sec-ch-ua-mobile': '?0',
          'sec-ch-ua-platform': '"macOS"',
          'sec-fetch-dest': 'empty',
          'sec-fetch-mode': 'cors',
          'sec-fetch-site': 'same-site',
        },
        referrer: 'https://app.netlify.com/sites/eventguest/forms/61b77c04c4895f0007bf9fcd',
        referrerPolicy: 'no-referrer-when-downgrade',
        body: null,
        method: 'GET',
        mode: 'cors',
        credentials: 'include',
      }
    ).then((res) => res.json())
  },
}
</script>

