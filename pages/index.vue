<template>
  <main>
    <section class="self-center flex flex-col flex-1 items-center justify-center">
      <h1 class="title text-center">This app was created using : Server side render websites using Nuxt.jsover postgres</h1>
      <h2 class="subtitle text-center">As a part of Web technology assignment, assigned by Nawaraj Paudel. Coded by Kushma Thapa, Masters in E-governance (76241008) </h2>
    </section>

    <section class="mt-8">
      <h3 class="text-primary-600 dark:text-primary-400 max-w-5xl mx-auto">Latest list of Guest of Event</h3>
      <posts post-type="blog" :amount="1" />
    </section>
  </main>
</template>