<template>
  <v-app>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  metaInfo: {
    title: 'INDEX'
  },
  meta: [
    { charset: 'utf-8' },
    { name: 'description', content: 'bot' },
    { name: 'viewport', content: 'width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0' }
  ],
  data: () => ({
    //
  }),
}
</script>
