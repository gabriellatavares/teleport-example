<script setup lang="ts">
import { ref } from 'vue'
import Layout from './components/Layout.vue'
import PrimaryModal from './components/PrimaryModal.vue'

const showModal = ref(false)
</script>

<template>
  <Layout>
    <h1>✨ Scoped Deferred Teleport</h1>
    <button @click="showModal = true">Open Modal</button>

    <PrimaryModal v-if="showModal" title="🚀 Primary Modal"
      content="This is the first modal. It can open another modal too!" @close="showModal = false" />
  </Layout>
</template>
