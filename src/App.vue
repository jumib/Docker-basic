<template>
  <v-app>
    <Nav/>
    <v-main>
      <HelloWorld/>
    </v-main>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import Nav from '@/components/Nav';

export default {
  name: 'App',

  components: {
    HelloWorld,
    Nav
  },

  data: () => ({
    //
  }),
};
</script>
