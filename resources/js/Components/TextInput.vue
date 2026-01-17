<script setup>
import { onMounted, ref } from 'vue';

const model = defineModel({
    type: String,
    required: true,
});

const input = ref(null);

onMounted(() => {
    if (input.value?.$el?.hasAttribute('autofocus')) {
        input.value.$el.focus();
    }
});

defineExpose({ focus: () => input.value?.$el?.focus() });
</script>

<template>
    <v-text-field
        v-model="model"
        ref="input"
    />
</template>
