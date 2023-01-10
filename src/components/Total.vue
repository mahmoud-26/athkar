<template>
  <div class="card">
    <h2 class="title">المجموع</h2>
    <hr>
    <div class="count">
      {{ total }}
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        total: 0
      }
    },
    methods: {
      getTotal() {
        setInterval(() => {
          this.total = parseInt(localStorage.getItem('id-1')) + parseInt(localStorage.getItem('id-2')) + parseInt(localStorage.getItem('id-3')) + parseInt(localStorage.getItem('id-4')) + parseInt(localStorage.getItem('id-5')) + parseInt(localStorage.getItem('id-6')) + parseInt(localStorage.getItem('id-7')) + parseInt(localStorage.getItem('id-8')) + parseInt(localStorage.getItem('id-9')) + parseInt(localStorage.getItem('id-10')) + parseInt(localStorage.getItem('id-11')) + parseInt(localStorage.getItem('id-12')) + parseInt(localStorage.getItem('id-13'))
        })
      }
    },
    mounted() {
      this.getTotal()
    }
  }
</script>

<style scoped>
  .card {
    margin-top: 2em;
    border: 1px solid black;
    border-radius: 10px;
    text-align: center;
    background: white;
    overflow: hidden;
    position: relative;
  }
  .count {
    padding: 1em 0;
    font-size: 1.25em;
    font-weight: 700;
  }
  hr {
    margin: 0;
    border: 0.5px solid lightgray;
  }
</style>