<template>
     <form @submit.prevent="submitNewContact">
          <div>
               <label>Name</label>
               <input type="text" v-model="newFriend.name"/>
          </div>
          <div>
               <label>Phone</label>
               <input type="tel" v-model="newFriend.phone"/>
          </div>
          <div>
               <label>E-Mail</label>
               <input type="email" v-model="newFriend.email"/>
          </div>
          <div>
               <button>Add Contact</button>
          </div>
     </form>
</template>

<script>
export default {
     // name: 'App',
     emits: ['add-contact'],
     data () {
          return {
               newFriend: {
                    name: '',
                    phone: '',
                    email: ''
               }
          }
     },
     methods: {
          submitNewContact () {
               this.$emit('add-contact', this.newFriend)
          }
     }
}
</script>

<style scoped></style>
