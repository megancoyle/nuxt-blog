<template>
  <header>
    <h2 class="logo">
      <NuxtLink to="/">WebDev</NuxtLink>
    </h2>
    <nav class="nav desktop">
      <ul>
        <li class="nav__list">
          <NuxtLink to="/blog">Blog</NuxtLink>
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
 