<template>
  <nav class="p-5 bg-green-400 text-white mb-10">
    <router-link :to="{ name: 'Home' }">Snazzy Fake Blog</router-link>
  </nav>
  <div class="container">
    <router-view />

    <div v-if="isLoading">Loaging...</div>

    <!-- This is the magic that makes the router-view work with Suspense -->
    <!-- <router-view v-slot="{ Component }">
      <template v-if="Component">
        <suspense>
          <template #default>
            <component :is="Component" />
          </template>
          <template #fallback>
            <div>Loading...</div>
          </template>
        </suspense>
      </template>
    </router-view> -->
  </div>
</template>

<script setup>
import usePageRequests from "./composables/usePageRequests";
const { isLoading } = usePageRequests();
</script>

<style lang="css">
.container {
  max-width: 960px;
  margin: 0 auto;
}
</style>
