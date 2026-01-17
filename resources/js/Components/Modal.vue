<script setup>
import { computed } from 'vue';

const props = defineProps({
    show: {
        type: Boolean,
        default: false,
    },
    maxWidth: {
        type: String,
        default: '2xl',
    },
    closeable: {
        type: Boolean,
        default: true,
    },
});

const emit = defineEmits(['close']);

const maxWidthValue = computed(() => {
    const mapping = {
        sm: '400',
        md: '500',
        lg: '600',
        xl: '700',
        '2xl': '800',
    };
    return mapping[props.maxWidth] || '800';
});

const handleClose = () => {
    if (props.closeable) {
        emit('close');
    }
};
</script>

<template>
    <v-dialog
        :model-value="show"
        :max-width="maxWidthValue"
        @update:model-value="(val) => !val && handleClose()"
        :persistent="!closeable"
    >
        <slot v-if="show" />
    </v-dialog>
</template>
