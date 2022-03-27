<template>
  <div class="row">
    <div class="col-2"></div>
    <div class="col-7">
      <story-card v-for="card in filterCards" :key="card.url" :info="card"/>
    </div>
    <div class="col-3"> 
      Sidebar 
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import StoryCard from "@/components/StoryCard.vue";
import store from "@/store.js";

let cards = [
  {
    "url": "https://picsum.photos/id/1/400/400",
    "description": "laptop",
    "time": "few minutes ago..."
  },
  {
    "url": "https://picsum.photos/id/2/400/400",
    "description": "laptop2",
    "time": "few hours ago..."
  },
  {
    "url": "https://picsum.photos/id/3/400/400",
    "description": "laptop3",
    "time": "few days ago..."
  },
  {
    "url": "https://picsum.photos/id/4/400/400",
    "description": "laptop4",
    "time": "few weeks ago..."
  },
]

export default {
  name: "HomeView",
  data: function() {
    return{
      cards,
      store
    }
  },
  components: {
    StoryCard,
  },
  computed: {
    filterCards() {
      let criteria = this.store.searchTerm;
      let newCards = [];
      for (let card of this.cards) {
        if(card.description.indexOf(criteria) >= 0)
          newCards.push(card)
      }
      return newCards;
    }
  },
};
</script>

<style scoped></style>
