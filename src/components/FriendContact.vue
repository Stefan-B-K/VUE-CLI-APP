<template>
  <li>
    <h2>{{ friend.name }}</h2>
    <button @click="toggleDetails">{{ showDetails ? 'Hide' : 'Show' }} Details</button>
    <ul v-if="showDetails">
      <li><strong>Phone: </strong>{{ friend.phone }}</li>
      <li><strong>Email: </strong>{{ friend.email }}</li>
    </ul>
  </li>
</template>

<script>
export default {
  name: 'FriendContact',
  data () {
    return {
      showDetails: false,
      friend: {
        id: 'manuel',
        name: 'Manuel Lopez',
        phone: '000 222 4444',
        email: 'manuel@mail.mm'
      },
    }
  },
  methods: {
    toggleDetails () {
      this.showDetails = !this.showDetails
    }
  }
}
</script>

<style scoped></style>
