<template>
  <main>
    <section v-if="posts" class="w-full max-w-5xl mx-auto">
      <h1 class="title">This app was created using : Server side render websites using Nuxt.jsover postgres, as a part of Web technology assignment, assigned by Nawaraj Paudel. Coded by Kushma Thapa, Masters in E-governance (76241008) </h1>
      <posts post-type="guest" :amount="10" />
    </section>
  </main>
</template>

<script>
export default {
  async asyncData({ $content, error }) {
    let posts;
    try {
      posts = await $content("guest").fetch();
    } catch (e) {
      error({ message: "Guest List not found" });
    }
    return { posts };
  },
}
</script>
