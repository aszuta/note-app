<template>
  <div>
    hello{{ message }}
    <div>
      <button @click="logout">logout</button>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      message: ''
    }
  },
  methods: {
    async logout () {
      await this.$auth.logout()
    },
    async mounted () {
      await this.$axios.get('/api/me')
      return this.message.name
    }
  }
}
</script>

<style>

</style>
