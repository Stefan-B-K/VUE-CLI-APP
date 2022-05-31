<template>
     <li>
          <h2>{{ friend.name }} {{ friend.isFavorite ? ' ︎♡' : '' }}</h2>
          <button @click="toggleFavorite">Toggle Favorite</button>
          <button @click="toggleDetails">{{ showDetails ? 'Hide' : 'Show' }} Details</button>
          <ul v-if="showDetails">
               <li><strong>Phone: </strong>{{ friend.phone }}</li>
               <li><strong>Email: </strong>{{ friend.email }}</li>
          </ul>
          <button @click="deleteContact">Delete</button>
     </li>
</template>

<script>
export default {
     // name: 'FriendContact',
     props: {
          friend: Object
     },
     emits: ['toggle-favorite', 'delete-contact'],                 // just to see clearly the emits of the component
     data () {
          return {
               showDetails: false,
          }
     },
     methods: {
          toggleDetails () {
               this.showDetails = !this.showDetails
          },
          toggleFavorite () {
               this.$emit('toggle-favorite', this.friend.id)
          },
          deleteContact() {
               this.$emit('delete-contact', this.friend.id)
          }
     }
}
</script>

<style scoped></style>

