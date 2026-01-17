<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import { Head, useForm } from '@inertiajs/vue3';

const form = useForm({
    password: '',
});

const submit = () => {
    form.post(route('password.confirm'), {
        onFinish: () => form.reset(),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Confirm Password" />

        <v-card>
            <v-card-title>Confirmar contraseña</v-card-title>

            <v-card-text>
                <div class="mb-4 text-body-2">
                    Esta es una área segura de la aplicación. Por favor, confirma tu contraseña antes de continuar.
                </div>

                <v-form @submit.prevent="submit">
                    <v-text-field
                        label="Password"
                        type="password"
                        v-model="form.password"
                        :error-messages="form.errors.password"
                        required
                        autocomplete="current-password"
                        autofocus
                    />

                    <div class="d-flex justify-end mt-4">
                        <v-btn type="submit" color="primary" :loading="form.processing">Confirmar</v-btn>
                    </div>
                </v-form>
            </v-card-text>
        </v-card>
    </GuestLayout>
</template>
