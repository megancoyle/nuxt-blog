<template>
  <header>
    <h2 class="logo">
      <nuxt-link to="/">WebDev</nuxt-link>
    </h2>
    <nav class="nav desktop">
      <ul>
        <li class="nav__list">
          <nuxt-link to="/blog">Blog</nuxt-link>
        </li>
      </ul>
    </nav>
  </header>
</template>
 
<script>
export default {
  name: 'Header'
  }
</script>
 