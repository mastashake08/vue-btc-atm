<template>
  <div class="text-center">
    <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          block rounded color=success x-large
          v-bind="attrs"
          v-on="on"
        >
          Sell ${{price}}
        </v-btn>
      </template>

      <v-card>
        <v-card-title class="headline grey lighten-2">
          Sell up to $200 of BTC on the lighting network!
        </v-card-title>

        <v-card-text>

        </v-card-text>

        <v-divider></v-divider>

        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn
            color="primary"
            text
            block
            @click="dialog = false"
          >
            Close
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  export default {
    props: ['price'],
    data () {
      return {
        dialog: false,
      }
    },
  }
</script>
