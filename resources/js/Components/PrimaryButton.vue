<script setup>
defineProps({
    type: {
        type: String,
        default: 'button',
    },
    disabled: {
        type: Boolean,
        default: false,
    },
    loading: {
        type: Boolean,
        default: false,
    },
});
</script>

<template>
    <v-btn
        :type="type"
        color="primary"
        :disabled="disabled"
        :loading="loading"
    >
        <slot />
    </v-btn>
</template>
