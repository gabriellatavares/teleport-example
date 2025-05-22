<script setup lang="ts">
import { ref } from 'vue'
import SecondaryModal from './SecondaryModal.vue'

const { title, content } = defineProps<{
    title: string
    content: string
}>()


defineEmits<(e: 'close') => void>()

const showNested = ref(false)
const visible = ref(true)
</script>

<template>
    <Teleport defer to="#modal-root">
        <Transition name="fade-zoom">
            <div v-if="visible" class="modal-wrapper">
                <div class="modal">
                    <h2>{{ title }}</h2>
                    <p>{{ content }}</p>
                    <button @click="showNested = true">Open Nested Modal</button>
                    <button @click="$emit('close')">Close</button>
                    <SecondaryModal v-if="showNested" @close="showNested = false" content="contest passed by prop!" />
                </div>
            </div>
        </Transition>
    </Teleport>
</template>



<style scoped>
.modal-wrapper {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.4);
    backdrop-filter: blur(4px);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1000;
}

.modal {
    background: white;
    padding: 2rem;
    border-radius: 1rem;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
    min-width: 300px;
    max-width: 90vw;
    transition: all 0.3s ease;
}

/* Transitions */
.fade-zoom-enter-active,
.fade-zoom-leave-active {
    transition: opacity 0.3s ease, transform 0.3s ease;
}

.fade-zoom-enter-from,
.fade-zoom-leave-to {
    opacity: 0;
    transform: scale(0.95);
}
</style>
