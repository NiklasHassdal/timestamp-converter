<script setup lang="ts">
defineProps<{ title: string }>();
</script>

<template>
    <div class="header">
        <div class="header-content">
            <h1 v-if="title">{{ title }}</h1>
            <slot />
        </div>
    </div>
</template>

<style scoped>
.header {
    width: 100%;
    height: 4rem;
    background-color: #222;
    filter: drop-shadow(0px 0px 4px #444)
}

.header-content {
    margin: 0 auto;
    padding: 0 0.5rem;
    max-width: 960px;
    width: 80%;
}

.header-content>h1 {
    margin: 0;
    padding: 0;
    font-size: 1.5rem;
    line-height: 4rem;
    color: #eee;
}

@media screen and (max-width: 768px) {
    .header-content {
        width: 100%;
    }
}
</style>