<template>
    <div class="layout">
        <slot></slot>

        <!-- Scoped teleport targets inside this layout -->
        <div id="modal-root"></div>
        <div id="overlay-root"></div>

    </div>
</template>

<style scoped>
.layout {
    position: relative;
    min-height: 100vh;
    padding: 2rem;
}

#modal-root,
#overlay-root {
    position: relative;
    z-index: 0;
    /* modals will still position themselves absolutely */
}
</style>
