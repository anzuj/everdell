<template>
  <v-app>
  
    <v-content>
      <ScoreCard/>
    </v-content>
  </v-app>
</template>

<script>
import ScoreCard from './components/ScoreCard';

export default {
  name: 'App',

  components: {
    ScoreCard,
  },

  data: () => ({
    //
  }),
};
</script>
