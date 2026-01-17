<script setup>
import { Link, useForm, usePage } from '@inertiajs/vue3';

defineProps({
    mustVerifyEmail: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const user = usePage().props.auth.user;

const form = useForm({
    name: user.name,
    email: user.email,
});
</script>

<template>
    <section>
        <header class="mb-6">
            <h2 class="text-h6 mb-2">Información de perfil</h2>
            <p class="text-body-2 text-medium-emphasis">
                Actualiza la información de tu perfil y la dirección de correo electrónico.
            </p>
        </header>

        <v-form @submit.prevent="form.patch(route('profile.update'))">
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

            <div v-if="mustVerifyEmail && user.email_verified_at === null" class="mt-4">
                <p class="text-body-2 mb-2">
                    Tu dirección de correo electrónico no está verificada.
                    <Link
                        :href="route('verification.send')"
                        method="post"
                        as="button"
                        class="text-decoration-none"
                    >
                        Haz clic aquí para reenviar el correo de verificación.
                    </Link>
                </p>

                <v-alert
                    v-show="status === 'verification-link-sent'"
                    type="success"
                    variant="tonal"
                    class="mt-2"
                >
                    Un nuevo enlace de verificación ha sido enviado a tu dirección de correo electrónico.
                </v-alert>
            </div>

            <div class="d-flex align-center gap-4 mt-4">
                <v-btn type="submit" color="primary" :loading="form.processing">Guardar</v-btn>
                <Transition enter-active-class="transition ease-in-out" enter-from-class="opacity-0" leave-active-class="transition ease-in-out" leave-to-class="opacity-0">
                    <span v-if="form.recentlySuccessful" class="text-body-2">Guardado.</span>
                </Transition>
            </div>
        </v-form>
    </section>
</template>
