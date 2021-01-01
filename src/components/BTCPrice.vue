<template>
  <v-container>
    Current BTC Price: ${{price}}
  </v-container>
</template>

<script>
  export default {
    name: 'BTCPrice',
    props: ['price'],
    data: () => ({
    })
  }
</script>
