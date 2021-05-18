<template>
  <div>
    <ul class="nav nav-tabs" id="myTab">
      <li class="nav-item nav-link">
        <nuxt-link to="/">List Posts</nuxt-link>
      </li>
      <li class="nav-item nav-link">
        <nuxt-link to="/contact">Contact</nuxt-link>
      </li>
      <li class="nav-item nav-link">
        <nuxt-link to="/about">About</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<style scoped>
a.nuxt-link-exact-active {
  font-weight: bold;
}
a.nuxt-link-exact-active {
  color: #00c58e;
}
a {
  text-decoration: none;
}
</style>