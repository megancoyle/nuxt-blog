<template>
  <main>
    <Header />
    <div class="container section">
      <div class="container__grid">
        <div v-for="article in articles" :key="article.slug + article.createdAt" class="card">
          <NuxtLink :to="`/blog/${article.slug}`">
            <img :src="article.cover_image" alt="article photographs"/>
          </NuxtLink>
          <div class="pad__card">
            <div class="author">
              <p class="author__name">{{ article.author }}</p> <span>|</span>
              <p>{{ article.date }}</p>
            </div>
            <NuxtLink :to="`/blog/${article.slug}`"><h2 class="title">{{ article.title }}</h2></NuxtLink>
            <p>{{
                article.description.substring(0, 150)
              }}...</p>
            <button>
              <NuxtLink :to="`/blog/${article.slug}`">Read More</NuxtLink>
            </button>
          </div>
        </div>
      </div>
    </div>

  </main>
</template>

<script>
export default {
  async asyncData({$content}) {
    const articles = await $content("articles").sortBy("publishOn", "desc").fetch()
    return {
      articles
    }
  },
  head() {
    return {
      title: "Learn More About Frontend Development",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: 'Learn more about various frontend frameworks and technologies.'
        }
      ]
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

.section {
  padding: 3em 0;
}

.container__grid {
  display: grid;
  gap: 2em;
  grid-template-columns: repeat(auto-fit, minmax(19rem, 1fr));
}

.card {
  background: #f7f9f8;
  box-shadow: 0px 4px 3px rgba(0, 0, 0, 0.1);
  border-radius: 5px;
}

.card img {
  object-fit: cover;
  border-top-left-radius: 5px;
  border-top-right-radius: 5px;
  width: 100%
}

.pad__card {
  padding: 2em;
}

.author {
  display: flex;
  align-items: center;
}

.author, .title {
  margin-bottom: 1em;
}

.author span {
  margin: 0 0.3em;
}

.author__name {
  text-transform: capitalize;
}

button {
  border: unset;
  padding: 1em 2em;
  margin-top: 2em;
  background: #0126cb;
  font-weight: 700;
  cursor: pointer;
}

button:hover {
  background: #011987;
}

button a {
  color: #fff;
}

.title {
  color: #111111;
}

.title:hover {
  color: #434242;
}
</style>