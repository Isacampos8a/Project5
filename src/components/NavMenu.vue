<template >
  <nav class="bg-yellow-200 p-5">
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/other">Other</RouterLink>
    <RouterLink to="/login">Login</RouterLink>
    <RouterLink to="/Settings">Settings</RouterLink>

  </nav>
</template>

<style lang="postcss" scoped>
nav {
  @apply flex justify-center space-x-4;

  & .router-link-active {
    @apply underline underline-offset-4;
  }
}
</style>
