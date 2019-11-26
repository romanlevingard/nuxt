<template>
    <section>
        <h1>{{pageTitle}}</h1>

      <ul>
          <Li v-for="user of users" :key="user.id">
             <a href="#" @click.prevent="openUser(user)">User {{user.name}}</a>
        </Li>
      </ul>
    
    </section>
</template>

<script>
export default {
  async  asyncData({$axios}) {
     const users = await $axios.$get('https://jsonplaceholder.typicode.com/users')
return{users}

    },
    data: () => ({
       pageTitle: 'Users Page'
    }),
    methods:{
        openUser(user){
            this.$router.push('/users/' + user.id)
        }

    }
}
</script>