<template>
     <section>
          <header><h1>My Friends</h1></header>
          <add-friend @add-contact="addContact"></add-friend>
          <ul>
               <friend-contact
                    v-for="friend in friends"
                    :key="friend.id"
                    :friend="friend"
                    @toggle-favorite="toggleFavorite"
                    @delete-contact="deleteContact">
               </friend-contact>
          </ul>
     </section>
</template>

<script>
export default {
     data () {
          return {
               friends: [
                    {
                         id: 'manuel',
                         name: 'Manuel Lopez',
                         phone: '000 222 4444',
                         email: 'manuel@mail.mm',
                         isFavorite: true
                    },
                    {
                         id: 'julie',
                         name: 'Julia Roberts',
                         phone: '000 333 6666',
                         email: 'julia@mail.mm',
                         isFavorite: false
                    },
               ]
          }
     },
     methods: {
          toggleFavorite (friendID) {
               const friendChanged = this.friends.find(friend => friend.id === friendID)
               friendChanged.isFavorite = !friendChanged.isFavorite
          },
          addContact (newFriend) {
               let id = newFriend.name.split(' ')[0].toLowerCase() + new Date().toISOString()
               console.log(id)
               const newContact = { ...newFriend, id }
               this.friends.push(newContact)
          },
          deleteContact(friendID) {
               this.friends = this.friends.filter(friend => friend.id !== friendID)
          }
     }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Jost&display=swap');

* {
     box-sizing: border-box;
}

html {
     font-family: 'Jost', sans-serif;
}

body {
     margin: 0;
}

header {
     box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
     margin: 3rem auto;
     border-radius: 10px;
     padding: 1rem;
     background-color: #58004d;
     color: white;
     text-align: center;
     width: 90%;
     max-width: 40rem;
}

#app ul {
     margin: 0;
     padding: 0;
     list-style: none;
}

#app li, #app form {
     box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
     margin: 1rem auto;
     border-radius: 10px;
     padding: 1rem;
     text-align: center;
     width: 90%;
     max-width: 40rem;
}

#app h2 {
     font-size: 2rem;
     border-bottom: 4px solid #ccc;
     color: #58004d;
     margin: 0 0 1rem 0;
}

#app button {
     font: inherit;
     cursor: pointer;
     border: 1px solid #ff0077;
     background-color: #ff0077;
     color: white;
     padding: 0.05rem 1rem;
     box-shadow: 1px 1px 2px rgba(0, 0, 0, 0.26);
}

#app button:hover,
#app button:active {
     background-color: #ec3169;
     border-color: #ec3169;
     box-shadow: 1px 1px 4px rgba(0, 0, 0, 0.26);
}

#app input {
     font: inherit;
     padding: 0.15rem;
}

#app label {
     font-weight: bold;
     margin-right: 1rem;
     width: 7rem;
     display: inline-block;
}

#app form div {
     margin: 1rem 0;
}
</style>
