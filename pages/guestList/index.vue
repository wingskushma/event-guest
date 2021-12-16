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
      <div v-else class="bg-white p-8 rounded-md w-full">
        <div class="flex items-center justify-between pb-12">
          <div>
            <h2 class="text-gray-600 font-semibold">Guest List</h2>
            <span class="text-xs"
              >This application is built using zapier so after each submission, it directs to deploy the app, therefore
              please wait a minute for your entry list to show up as it takes a minute or two for tha application to be
              published with new submission.</span
            >
          </div>
        </div>
        <div>
          <div class="-mx-4 sm:-mx-8 px-4 sm:px-8 py-4 overflow-x-auto">
            <div class="inline-block min-w-full shadow rounded-lg overflow-hidden">
              <table class="min-w-full leading-normal">
                <thead>
                  <tr>
                    <th
                      class="
                        px-5
                        py-3
                        border-b-2 border-gray-200
                        bg-gray-100
                        text-left text-xs
                        font-semibold
                        text-gray-600
                        uppercase
                        tracking-wider
                      "
                    >
                      Name
                    </th>
                    <th
                      class="
                        px-5
                        py-3
                        border-b-2 border-gray-200
                        bg-gray-100
                        text-left text-xs
                        font-semibold
                        text-gray-600
                        uppercase
                        tracking-wider
                      "
                    >
                      Email
                    </th>
                    <th
                      class="
                        px-5
                        py-3
                        border-b-2 border-gray-200
                        bg-gray-100
                        text-left text-xs
                        font-semibold
                        text-gray-600
                        uppercase
                        tracking-wider
                      "
                    >
                      Address
                    </th>
                    <th
                      class="
                        px-5
                        py-3
                        border-b-2 border-gray-200
                        bg-gray-100
                        text-left text-xs
                        font-semibold
                        text-gray-600
                        uppercase
                        tracking-wider
                      "
                    >
                      Role
                    </th>
                  </tr>
                </thead>
                <tbody>
                  <tr v-for="(userData, index) in usersData" :key="index">
                    <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                      <div class="flex items-center">
                        <div class="ml-3">
                          <p class="text-gray-900 whitespace-no-wrap">
                            {{ userData.data.fullname }}
                          </p>
                        </div>
                      </div>
                    </td>
                    <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                      <p class="text-gray-900 whitespace-no-wrap">{{ userData.data.email }}</p>
                    </td>
                    <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                      <p class="text-gray-900 whitespace-no-wrap">
                        {{ userData.data.address }}
                      </p>
                    </td>
                    <td class="px-5 py-5 border-b border-gray-200 bg-white text-sm">
                      <span class="relative inline-block px-3 py-1 font-semibold text-green-900 leading-tight">
                        <span aria-hidden class="absolute inset-0 bg-green-200 opacity-50 rounded-full"></span>
                        <span class="relative">{{ userData.data.role }}</span>
                      </span>
                    </td>
                  </tr>
                </tbody>
              </table>
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
export default {
  data() {
    return {
      usersData: [],
    }
  },
  async fetch() {
    const { API_TOKEN } = process.env
    this.usersData = await fetch(
      'https://api.netlify.com/api/v1/sites/eventguest/forms/61b77c04c4895f0007bf9fcd/submissions',
      {
        headers: {
          accept: '*/*',
          authorization: 'Bearer tO_M-Vp-V7tbtwxEnHXH4vOTHozUAaebSrxm90PtfrQ',
          'content-type': 'application/json',
        },
        referrer: 'https://app.netlify.com/sites/eventguest/forms/61b77c04c4895f0007bf9fcd',
        referrerPolicy: 'no-referrer-when-downgrade',
        method: 'GET',
      }
    ).then((res) => res.json())
  },
}
</script>

