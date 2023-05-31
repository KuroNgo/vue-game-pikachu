<template>
  <main-screen v-if="statusMatch === 'default'" @onStart="onHandleBeforeStart($event)" />
  <interact-screen v-if="statusMatch === 'match'" />
</template>

<script>
import InteractScreen from './components/InteractScreen.vue';
import MainScreen from './components/MainScreen.vue';
export default {
  name: 'App',
  data() {
    return {
      settings: {
        totalOfBlocks: 0,
        cardsContext: [],
      },
      statusMatch: "default",
    }
  },
  components: {
    MainScreen,
    InteractScreen
  },
  methods: {
    onHandleBeforeStart(config) {
      console.log("running handle before start", config)
      this.settings.totalOfBlocks = config.totalOfBlocks;

      const firstCards = Array.from(
        { length: this.settings.totalOfBlocks / 2 },
        (_, i) => i + 1
      );
      console.log(firstCards);
      // const secondCards = [...firstCards];
      // const cards =[...firstCards,...secondCards];
      // this.settings.cardsContext= shuffled(shuffled(shuffled(shuffled(cards))));
      // console.log(this.settings.cardsContext)
      // data ready
      this.statusMatch = "match"
    }
  }
}
</script>

