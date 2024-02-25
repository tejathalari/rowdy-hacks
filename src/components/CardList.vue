<template>
    <div class="container mx-auto py-8 flex justify-center items-center">
      <div class="grid grid-cols-1 gap-4" style="width: 50%;">
        <Card v-for="(card, index) in cards" :key="card.id" :data="card" :expanded="index === expandedIndex" @expand="expandCard(index)" />
      </div>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  import Card from './Card.vue';
  
  export default {
    components: {
      Card
    },
    data() {
      return {
        cards: [],
        expandedIndex: -1
      };
    },
    mounted() {
      this.fetchCards();
    },
    methods: {
      async fetchCards() {
        try {
          const response = await axios.get('https://jsonplaceholder.typicode.com/posts');
          this.cards = response.data;
        } catch (error) {
          console.error('Error fetching cards:', error);
        }
      },
      expandCard(index) {
        if (this.expandedIndex === index) {
          this.expandedIndex = -1; // Collapse the card if it's already expanded
        } else {
          this.expandedIndex = index;
          // Collapse all other cards
          this.collapseOtherCards(index);
        }
      },
      collapseOtherCards(index) {
        for (let i = 0; i < this.cards.length; i++) {
          if (i !== index) {
            this.$set(this.cards, i, {...this.cards[i], expanded: false});
          }
        }
      }
    }
  }
  </script>
  