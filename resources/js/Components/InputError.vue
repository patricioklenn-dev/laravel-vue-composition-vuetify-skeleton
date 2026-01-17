<script setup>
defineProps({
    message: {
        type: String,
    },
});
</script>

<template>
    <div v-show="message">
        <p class="text-caption text-error">
            {{ message }}
        </p>
    </div>
</template>
