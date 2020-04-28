<template>
  <v-container>
    <v-row class="text-center">
      <v-col cols="12">
        <v-card class="mx-auto" max-width="400">
          <v-img
            class="white--text align-end"
            height="90px"
            position="top center"
            :src="require('../assets/images/classic.jpg')"
          ></v-img>

          <v-card-text class="text--primary">
            <!-- table -->
            <v-data-table
              :headers="headers"
              :items="pointItems"
              disable-pagination
              disable-sort
              hide-default-footer
            >
              <template v-slot:item.points1="props">
                <v-edit-dialog :return-value.sync="props.item.points1">
                  {{ props.item.points1 }}
                  <template v-slot:input>
                    <v-text-field v-model="props.item.points1" single-line></v-text-field>
                  </template>
                </v-edit-dialog>
              </template>

              <template v-slot:item.points2="props">
                <v-edit-dialog :return-value.sync="props.item.points2">
                  {{ props.item.points2 }}
                  <template v-slot:input>
                    <v-text-field v-model="props.item.points2" single-line></v-text-field>
                  </template>
                </v-edit-dialog>
              </template>
            </v-data-table>
            <v-divider></v-divider>
            <!-- /table -->

            <v-row class="yellow lighten-4 mx-0">
              <v-col class="mx-4" align="start">Total:</v-col>
              <v-col class="ml-2" align="start">{{ player1score }}</v-col>
              <v-col align="start">{{ player2score }}</v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "ScoreCard",

  data: () => ({
    score1: 0,
    score2: 0,
    headers: [
      {
        text: "Card items",
        align: "start",
        value: "item"
      },
      { text: "Player 1", value: "points1" },
      { text: "Player 2", value: "points2" }
    ],

    pointItems: [
      {
        item: "Cards",
        points1: "",
        points2: ""
      },
      {
        item: "Prosperity",
        points1: "",
        points2: ""
      },
      {
        item: "Events",
        points1: "",
        points2: ""
      },
      {
        item: "Gold",
        points1: "",
        points2: ""
      },
      {
        item: "Journey",
        points1: "",
        points2: ""
      }
    ]
  }),

  methods: {},
  computed: {
    player1score() {
      let total = 0;
      for (const el of this.pointItems) {
        total += Number(el.points1);
      }
      return total;
    },
       player2score() {
      let total = 0;
      for (const el of this.pointItems) {
        total += Number(el.points2);
      }
      return total;
    }
  }
};
</script>

<style scoped>
/* .v-data-table .text-start{
  text-align: center !important;
} */
</style>
