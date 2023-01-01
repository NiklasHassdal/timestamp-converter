<template>
    <div class="container">
        <slot />
    </div>
</template>

<style scoped>
.container {
    margin: 0.5rem auto;
    padding: 0.5rem;
    width: 80%;
    max-width: 960px;
    background-color: #fff;
}

@media screen and (max-width: 768px) {
    .container {
        margin: 0.25rem auto;
        padding: 0.25rem;
        width: 100%;
    }
}
</style>