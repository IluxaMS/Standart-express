<template>
    <button class="app-button" :class="[`app-button--${size}`, { 'app-button--outline': outline }]">
        {{ label }}
    </button>
</template>

<script setup lang="ts">
interface Props {
    label: string;
    size?: 'sm' | 'md' | 'lg' | 'sc';
    outline?: boolean;
}

withDefaults(defineProps<Props>(), {
    size: 'md',
    outline: false,
});
</script>

<style scoped lang="scss">
.app-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    border-radius: 50px;
    font-family: "Euclid Circular A", sans-serif;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.2s ease-in-out;
    background-color: #ED9121;
    color: #FFFFFF;

    &:hover {
        filter: brightness(1.1);
    }

    &:active {
        transform: scale(0.96);
    }

    &--outline {
        background-color: transparent;
        color: #ED9121;
        border: 1px solid #ED9121;
    }

    &--sm {
        padding: 8px 16px;
        font-size: 14px;
        min-width: 100px;
        height: 50px;
    }

    &--md {
        padding: 16px 12px;
        font-size: 12px;
    }

    &--lg {
        padding: 16px 32px;
        font-size: 18px;
    }

    &--sc {
        padding: 8px 16px;
        font-size: 14px;
        max-width: 129px;
        height: 50px;
    }
}
</style>