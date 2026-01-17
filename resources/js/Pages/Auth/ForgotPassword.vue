<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, useForm } from '@inertiajs/vue3';

defineProps({
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
});

const submit = () => {
    form.post(route('password.email'));
};
</script>

<template>
    <GuestLayout>
        <Head title="Forgot Password" />

        <v-card>
            <v-card-title>Forgot Password</v-card-title>

            <v-card-text>
                <div class="mb-4 text-body-2">
                    Olvidaste tu contraseña? No hay problema. Simplemente dínos tu dirección de correo electrónico y te enviaremos un enlace de restablecimiento de contraseña que te permitirá elegir una nueva.
                </div>

                <v-alert v-if="status" type="success" class="mb-4">
                    {{ status }}
                </v-alert>

                <v-form @submit.prevent="submit">
                    <v-text-field
                        label="Email"
                        type="email"
                        v-model="form.email"
                        :error-messages="form.errors.email"
                        required
                        autofocus
                        autocomplete="username"
                    />

                    <div class="d-flex justify-end mt-4">
                        <v-btn type="submit" color="primary" :loading="form.processing">Enviar enlace de restablecimiento de contraseña</v-btn>
                    </div>
                </v-form>
            </v-card-text>
        </v-card>
    </GuestLayout>
</template>
