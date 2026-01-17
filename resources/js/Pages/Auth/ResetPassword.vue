<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, useForm } from '@inertiajs/vue3';

const props = defineProps({
    email: {
        type: String,
        required: true,
    },
    token: {
        type: String,
        required: true,
    },
});

const form = useForm({
    token: props.token,
    email: props.email,
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('password.store'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Reset Password" />

        <v-card>
            <v-card-title>Restablecer contraseña</v-card-title>

            <v-card-text>
                <v-form @submit.prevent="submit">
                    <v-text-field
                        label="Correo electrónico"
                        type="email"
                        v-model="form.email"
                        :error-messages="form.errors.email"
                        required
                        autofocus
                        autocomplete="username"
                    />

                    <v-text-field
                        label="Contraseña"
                        type="password"
                        v-model="form.password"
                        :error-messages="form.errors.password"
                        required
                        autocomplete="new-password"
                    />

                    <v-text-field
                        label="Confirmar contraseña"
                        type="password"
                        v-model="form.password_confirmation"
                        :error-messages="form.errors.password_confirmation"
                        required
                        autocomplete="new-password"
                    />

                    <div class="d-flex justify-end mt-4">
                        <v-btn type="submit" color="primary" :loading="form.processing">Restablecer contraseña</v-btn>
                    </div>
                </v-form>
            </v-card-text>
        </v-card>
    </GuestLayout>
</template>
