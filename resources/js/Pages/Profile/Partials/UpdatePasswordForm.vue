<script setup>
import { useForm } from '@inertiajs/vue3';
import { ref } from 'vue';

const passwordInput = ref(null);
const currentPasswordInput = ref(null);

const form = useForm({
    current_password: '',
    password: '',
    password_confirmation: '',
});

const updatePassword = () => {
    form.put(route('password.update'), {
        preserveScroll: true,
        onSuccess: () => form.reset(),
        onError: () => {
            if (form.errors.password) {
                form.reset('password', 'password_confirmation');
                passwordInput.value.focus();
            }
            if (form.errors.current_password) {
                form.reset('current_password');
                currentPasswordInput.value.focus();
            }
        },
    });
};
</script>

<template>
    <section>
        <header class="mb-6">
            <h2 class="text-h6 mb-2">Actualizar contraseña</h2>
            <p class="text-body-2 text-medium-emphasis">
                Asegura que tu cuenta esté usando una contraseña larga y aleatoria para mantenerse segura.
            </p>
        </header>

        <v-form @submit.prevent="updatePassword">
            <v-text-field
                label="Contraseña actual"
                ref="currentPasswordInput"
                v-model="form.current_password"
                type="password"
                :error-messages="form.errors.current_password"
                autocomplete="current-password"
            />

            <v-text-field
                label="Nueva contraseña"
                ref="passwordInput"
                v-model="form.password"
                type="password"
                :error-messages="form.errors.password"
                autocomplete="new-password"
            />

            <v-text-field
                label="Confirmar contraseña"
                v-model="form.password_confirmation"
                type="password"
                :error-messages="form.errors.password_confirmation"
                autocomplete="new-password"
            />

            <div class="d-flex align-center gap-4 mt-4">
                <v-btn type="submit" color="primary" :loading="form.processing">Guardar</v-btn>
                <Transition enter-active-class="transition ease-in-out" enter-from-class="opacity-0" leave-active-class="transition ease-in-out" leave-to-class="opacity-0">
                    <span v-if="form.recentlySuccessful" class="text-body-2">Guardado.</span>
                </Transition>
            </div>
        </v-form>
    </section>
</template>
