<template>
  <main>
    <section class="w-full max-w-5xl mx-auto">
      <h1 class="title">Guest Entry Form</h1>
    </section>
    <section class="w-full max-w-5xl mx-auto">
      <form
        class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4"
        name="guestEntry"
        method="POST"
        data-netlify="true"
        data-netlify-honeypot="bot-field"
        @submit.prevent="handleSubmit"
      >
        <input type="hidden" name="form-name" value="guestEntry" />
        <div class="mb-4">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="fullname"> Your Name </label>
          <input
            class="
              shadow
              appearance-none
              border
              rounded
              w-full
              py-2
              px-3
              text-gray-700
              leading-tight
              focus:outline-none focus:shadow-outline
            "
            id="fullname"
            type="text"
            placeholder="Full Name"
          />
        </div>
        <div class="mb-6">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="address"> Your Address </label>
          <input
            class="
              shadow
              appearance-none
              border
              rounded
              w-full
              py-2
              px-3
              text-gray-700
              leading-tight
              focus:outline-none focus:shadow-outline
            "
            id="address"
            type="text"
            placeholder="Address"
          />
        </div>

        <div class="mb-6">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="email"> Your Email </label>
          <input
            class="
              shadow
              appearance-none
              border
              rounded
              w-full
              py-2
              px-3
              text-gray-700
              leading-tight
              focus:outline-none focus:shadow-outline
            "
            id="email"
            type="email"
            placeholder="Email"
          />
        </div>

        <div class="mb-6">
          <label class="block text-gray-700 text-sm font-bold mb-2" for="email"> Your Gender </label>
          <select
            name="role"
            class="
              shadow
              appearance-none
              border
              rounded
              w-full
              py-2
              px-3
              text-gray-700
              leading-tight
              focus:outline-none focus:shadow-outline
            "
            id="gender"
          >
            <option value="male">Male</option>
            <option value="female">Female</option>
            <option value="other">Other</option>
          </select>
        </div>
        <div class="flex items-center justify-between">
          <button
            class="
              bg-blue-500
              hover:bg-blue-700
              text-white
              font-bold
              py-2
              px-4
              rounded
              focus:outline-none focus:shadow-outline
            "
            type="button"
          >
            Confirm Attendance
          </button>
        </div>
      </form>
      <p class="text-center text-gray-500 text-xs">&copy;2021 Kushma Thapa All rights reserved.</p>
    </section>
  </main>
</template>

<script>
function encode(data) {
  return Object.keys(data)
    .map((key) => encodeURIComponent(key) + '=' + encodeURIComponent(data[key]))
    .join('&')
}

const handleSubmit = (event) => {
  event.preventDefault()
  fetch('/', {
    method: 'POST',
    headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
    body: encode({
      'form-name': event.target.getAttribute('name'),
      ...name,
    }),
  })
    .then(() => navigate('/thanks/'))
    .catch((error) => alert(error))
}
</script>
