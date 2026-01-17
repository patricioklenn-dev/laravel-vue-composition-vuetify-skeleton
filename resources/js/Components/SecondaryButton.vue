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
});
</script>

<template>
    <v-btn
        :type="type"
        variant="outlined"
        :disabled="disabled"
    >
        <slot />
    </v-btn>
</template>
