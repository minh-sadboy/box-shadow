<template>
  <div class="header-wrap">
    <ul>
      <li>
        <NuxtLink to="/box-shadow">Box shadow</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/text-shadow">Text shadow</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/border">Border</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/transform">Transform</NuxtLink>
      </li>
      <li>
        <NuxtLink to="/gradient">Gradient</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style lang="scss" scoped>
.header-wrap {
  background-color: $white;

  ul {
    list-style: none;
    text-align: center;
    padding: 20px 0;

    li {
      display: inline-block;
      padding: 3px 10px;

      a {
        color: $black;
        text-decoration: none;
        font-size: 1rem;
        &:hover {
          color: $blue;
        }
        &.nuxt-link-exact-active {
          color: $blue;
        }
      }
    }
  }
}
</style>
