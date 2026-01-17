<template>
    <v-app>
      <v-main>
        <v-container class="fill-height" fluid>
          <v-row align="center" justify="center">
            <v-col cols="12" sm="6" md="4">
              <slot />
            </v-col>
          </v-row>
        </v-container>
      </v-main>
    </v-app>
  </template>
  