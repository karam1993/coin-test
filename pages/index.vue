<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card class="logo py-4 d-flex justify-center">
        <VuetifyLogo />
      </v-card>
      <v-card>
        <v-card-title class="headline mt-2">
          <v-icon class="mx-2">mdi-bitcoin</v-icon> Coins Price
        </v-card-title>
       
        <v-card-actions>
          <v-spacer />
          <v-btn
            color="primary"
            nuxt
            to="/coins"
          >
            Go
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'IndexPage'
}
</script>
