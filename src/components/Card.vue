<template>
  <div class="card">
    <i class="fi fi-rr-info info" v-if="show" @click="showInfo"></i>
    <i class="fi fi-rr-refresh reset" v-if="show" @click="resetData"></i>
    <h2 class="title" @click="toggleShow"><slot /></h2>
    <hr>
    <div class="count" @click="increase">
      {{ count }}
    </div> 
  </div>
</template>

<script>
  import Swal from 'sweetalert2'
  
  export default {
    props: ['id', 'info'],
    data() {
      return {
        count: 0,
        show: false
      }
    },
    methods: {
      increase() {
        this.count++
        localStorage.setItem(`id-${this.id}`, this.count)
      },
      toggleShow() {
        this.show = !this.show
      },
      resetData() {
        Swal.fire({
          title: 'هل تريد مسح هذه البيانات؟',
          showConfirmButton: false,
          showDenyButton: true,
          showCancelButton: true,
          denyButtonText: 'مسح',
          cancelButtonText: `إلغاء`,
        }).then((result) => {
          if (result.isDenied) {
            Swal.fire({
              title: 'تم المسح بنجاح',
              icon: 'success',
              confirmButtonText: 'حسنًا'
            })
            this.count = 0
            localStorage.setItem(`id-${this.id}`, 0)
         }
        })
      },
      showInfo() {
        Swal.fire({
          title: this.info,
          confirmButtonText: 'حسنًا'
        })
      }
    },
    mounted() {
      if (localStorage.getItem(`id-${this.id}`) == null) {
        this.count = 0;
        localStorage.setItem(`id-${this.id}`, this.count);
      } else {
        this.count = parseInt(localStorage.getItem(`id-${this.id}`))
      }
      localStorage.removeItem('id-undefined')
    },
    unmounted() {
      localStorage.removeItem(`id-${this.id}`)
      localStorage.removeItem('id-undefined')
    }
  }
</script>

<style scoped>
  .card {
    border: 1px solid black;
    border-radius: 10px;
    text-align: center;
    background: white;
    overflow: hidden;
    position: relative;
  }
  .card:not(:nth-of-type(1)) {
    margin-top: 2em;
  }
  .title {
    padding: 1em;
  }
  .reset {
    position: absolute;
    top: 0.5em;
    left: 0.5em;
    color: gray;
  }
  .info {
    position: absolute;
    top: 0.5em;
    right: 0.5em;
    color: gray;
  }
  .reset:active {
    color: black;
  }
  .info:active {
    color: black;
  }
  .count {
    padding: 1em 0;
    font-size: 1.25em;
    font-weight: 700;
  }
  .count:active {
    background: ghostwhite;
  }
  hr {
    margin: 0;
    border: 0.5px solid lightgray;
  }
</style>