<template>
    <v-app>
        <v-app-bar color="primary" dark>
            <v-app-bar-title>Laravel</v-app-bar-title>
            <v-spacer />
            <v-btn text @click="$inertia.visit(route('dashboard'))">Panel de control</v-btn>
            <v-btn text @click="$inertia.visit(route('profile.edit'))">Perfil</v-btn>
            <v-btn text @click="$inertia.post(route('logout'))">Cerrar sesión</v-btn>
        </v-app-bar>
        <v-main>
            <slot />
        </v-main>
    </v-app>
</template>
  