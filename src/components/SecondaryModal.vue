<script setup lang="ts">
import { ref } from 'vue'

const { title = 'Default title here! 😎', content } = defineProps<{
    title?: string
    content: string
}>()


defineEmits<(e: 'close') => void>()

const visible = ref(true)

</script>

<template>
    <teleport defer to="#overlay-root">
        <transition name="fade-zoom">
            <div v-if="visible" class="modal-wrapper">
                <div class="modal">
                    <h2>{{ title }}</h2>
                    <p>{{ content }}</p>
                    <button @click="$emit('close')">Close Nested Modal</button>
                </div>
            </div>
        </transition>
    </teleport>
</template>



<style scoped>
.modal-wrapper {
    position: fixed;
    inset: 0;
    background: rgba(0, 0, 0, 0.3);
    backdrop-filter: blur(2px);
    display: flex;
    align-items: center;
    justify-content: center;
    z-index: 1100;
}

.modal {
    background: white;
    padding: 1.5rem;
    border-radius: 1rem;
    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
    min-width: 260px;
}

/* Reuse transition from PrimaryModal */
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
