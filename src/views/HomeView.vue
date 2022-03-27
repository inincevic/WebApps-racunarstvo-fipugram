<template>
  <div class="row">
    <div class="col-2"></div>
    <div class="col-7">
      <story-card v-for="card in cards" :key="card" :info="card"/>
    </div>
    <div class="col-3"> 
      Sidebar
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import StoryCard from "@/components/StoryCard.vue";

let cards = [
  "https://picsum.photos/id/1/400/400",
  "https://picsum.photos/id/2/400/400",
  "https://picsum.photos/id/3/400/400",
  "https://picsum.photos/id/4/400/400"
]

export default {
  name: "HomeView",
  data: function() {
    return{
      cards
    }
  },
  components: {
    StoryCard,
  },
};
</script>

<style scoped></style>
