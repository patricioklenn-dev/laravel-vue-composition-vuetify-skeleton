<script setup>
import { computed } from 'vue';
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const props = defineProps({
    status: {
        type: String,
    },
});

const form = useForm({});

const submit = () => {
    form.post(route('verification.send'));
};

const verificationLinkSent = computed(() => props.status === 'verification-link-sent');
</script>

<template>
    <GuestLayout>
        <Head title="Email Verification" />

        <v-card>
            <v-card-title>Verificación de correo electrónico</v-card-title>

            <v-card-text>
                <div class="mb-4 text-body-2">
                    Gracias por registrarte! Antes de empezar, podrías verificar tu dirección de correo electrónico haciendo clic en el enlace
                    que te acabamos de enviar? Si no recibiste el correo, te enviaremos otro.
                </div>

                <v-alert v-if="verificationLinkSent" type="success" class="mb-4">
                    Un nuevo enlace de verificación ha sido enviado a la dirección de correo electrónico que proporcionaste durante el registro.
                </v-alert>

                <v-form @submit.prevent="submit">
                    <div class="d-flex justify-space-between align-center mt-4">
                        <v-btn type="submit" color="primary" :loading="form.processing">Reenviar correo de verificación</v-btn>
                        <Link :href="route('logout')" method="post" as="button" class="text-decoration-none">Cerrar sesión</Link>
                    </div>
                </v-form>
            </v-card-text>
        </v-card>
    </GuestLayout>
</template>
