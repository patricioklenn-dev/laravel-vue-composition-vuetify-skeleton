<script setup>
    import GuestLayout from '@/Layouts/GuestLayout.vue'
    import { useForm } from '@inertiajs/vue3'
    
    const form = useForm({
      email: '',
      password: '',
      remember: false,
    })
    
    const submit = () => {
      form.post(route('login'))
    }
    </script>
    
    <template>
      <GuestLayout>
        <v-card>
          <v-card-title>Iniciar sesión</v-card-title>
    
          <v-card-text>
            <v-form @submit.prevent="submit">
              <v-text-field
                label="Email"
                v-model="form.email"
                :error-messages="form.errors.email"
              />
    
              <v-text-field
                label="Contraseña"
                type="password"
                v-model="form.password"
                :error-messages="form.errors.password"
              />
    
              <v-checkbox
                label="Recordarme"
                v-model="form.remember"
              />
    
              <v-btn
                type="submit"
                color="primary"
                block
                :loading="form.processing"
              >
                Entrar
              </v-btn>
            </v-form>
          </v-card-text>
        </v-card>
      </GuestLayout>
    </template>
    