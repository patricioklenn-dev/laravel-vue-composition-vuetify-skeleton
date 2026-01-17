<script setup>
import { useForm } from '@inertiajs/vue3';
import { nextTick, ref } from 'vue';

const confirmingUserDeletion = ref(false);
const passwordInput = ref(null);

const form = useForm({
    password: '',
});

const confirmUserDeletion = () => {
    confirmingUserDeletion.value = true;

    nextTick(() => passwordInput.value.focus());
};

const deleteUser = () => {
    form.delete(route('profile.destroy'), {
        preserveScroll: true,
        onSuccess: () => closeModal(),
        onError: () => passwordInput.value.focus(),
        onFinish: () => form.reset(),
    });
};

const closeModal = () => {
    confirmingUserDeletion.value = false;

    form.reset();
};
</script>

<template>
    <section>
        <header class="mb-6">
            <h2 class="text-h6 mb-2">Eliminar cuenta</h2>
            <p class="text-body-2 text-medium-emphasis">
                Una vez que se elimine tu cuenta, todos sus recursos y datos se eliminarán permanentemente. Antes de eliminar
                tu cuenta, por favor descarga cualquier dato o información que desees conservar.
            </p>
        </header>

        <v-btn color="error" @click="confirmUserDeletion">Eliminar cuenta</v-btn>

        <v-dialog v-model="confirmingUserDeletion" max-width="500" @update:model-value="(val) => !val && closeModal()">
            <v-card>
                <v-card-title>
                    ¿Estás seguro de querer eliminar tu cuenta?
                </v-card-title>

                <v-card-text>
                    <p class="text-body-2 mb-4">
                        Una vez que se elimine tu cuenta, todos sus recursos y datos se eliminarán permanentemente. Por favor
                        ingresa tu contraseña para confirmar que deseas eliminar tu cuenta permanentemente.
                    </p>

                    <v-text-field
                        ref="passwordInput"
                        v-model="form.password"
                        type="password"
                        label="Contraseña"
                        placeholder="Contraseña"
                        :error-messages="form.errors.password"
                        @keyup.enter="deleteUser"
                    />
                </v-card-text>

                <v-card-actions>
                    <v-spacer />
                    <v-btn @click="closeModal">Cancelar</v-btn>
                    <v-btn color="error" :loading="form.processing" @click="deleteUser">Eliminar cuenta</v-btn>
                </v-card-actions>
            </v-card>
        </v-dialog>
    </section>
</template>
