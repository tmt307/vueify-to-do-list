<template>
  <v-app>


    <v-content>
      <HelloWorld/>
    </v-content>
  </v-app>
</template>

<script>
import todoapp from './components/todoapp';

export default {
  name: 'App',
  components: {
    todoapp,
  },
  data: () => ({
    //
  }),
};
</script>
