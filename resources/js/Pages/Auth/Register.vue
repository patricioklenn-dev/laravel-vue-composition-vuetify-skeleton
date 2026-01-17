<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, Link, useForm } from '@inertiajs/vue3';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Register" />

        <v-card>
            <v-card-title>Registrar</v-card-title>

            <v-card-text>
                <v-form @submit.prevent="submit">
                    <v-text-field
                        label="Nombre"
                        v-model="form.name"
                        :error-messages="form.errors.name"
                        required
                        autofocus
                        autocomplete="name"
                    />

                    <v-text-field
                        label="Correo electrónico"
                        type="email"
                        v-model="form.email"
                        :error-messages="form.errors.email"
                        required
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

                    <div class="d-flex justify-space-between align-center mt-4">
                        <Link :href="route('login')" class="text-decoration-none">Ya tienes una cuenta?</Link>
                        <v-btn type="submit" color="primary" :loading="form.processing">Registrar</v-btn>
                    </div>
                </v-form>
            </v-card-text>
        </v-card>
    </GuestLayout>
</template>
