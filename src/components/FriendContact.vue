<template>
  
    <h2>{{ friendName }}</h2>
    <button @click="toggleDetails">{{ detailsAreVisible ? 'Hide' : 'Show' }} Details</button>

    <button @click="deleteItem"> Delete </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>Phone:</strong>
        {{ friendPhone }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ friendEmail }}
      </li>
    </ul>
 
</template>

<script>
export default {
  props:[
          "friendName",
          "friendEmail",
          "friendPhone",
          "friendId"
        ],
          
  data() {
    return {
      detailsAreVisible: false,
  
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },

    deleteItem(){

      this.$emit('delete-event',this.friendId)
    }
  }
};
</script>