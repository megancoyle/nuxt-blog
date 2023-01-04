<template>
  <main>
    <Header />
    <div class="container">
      <div class="return">
        <NuxtLink to="/">Home</NuxtLink>
        <span>/</span>
        <NuxtLink to="/blog">Blog</NuxtLink>
        <span>/</span>
        <p>{{ note.title.substring(0, 15) }}...</p>
      </div>
      <section>
        <h1>{{ note.title }}</h1>
        <img :src="note.cover_image" alt="article photographs"/>
        <NuxtContent :document="note" cla />
      </section>
    </div>
  </main>
</template>

<script>
export default {
  async asyncData({$content, route}) {
    const note = await $content(`articles/${route.params.slug}`).fetch()
    return {
      note
    }
  }
}
</script>

<style scoped>
header {
  background: #111111;
  position: unset;
}

.container {
  width: 85%;
  max-width: 75rem;
  margin-inline: auto;
}

section {
  padding-bottom: 2em;
}

.return {
  display: flex;
  margin: 1.5em 0;
}

.return img {
  width: 20px;
  height: 20px;
}

.return span {
  margin: 0 1em;
}

h1 {
  margin-bottom: 1em
}
</style>

<style>
.nuxt-content h2, .nuxt-content p {
  margin-top: 1em;
}
</style>
