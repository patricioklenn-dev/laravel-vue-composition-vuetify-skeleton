<script setup>
defineProps({
    value: {
        type: String,
    },
    for: {
        type: String,
    },
});
</script>

<template>
    <v-label :for="for">
        <span v-if="value">{{ value }}</span>
        <span v-else><slot /></span>
    </v-label>
</template>
