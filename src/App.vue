<template>
  <div class="container my-5 text-center">
    <h1 class="text-secondary">Cuenta regresiva</h1>
    <p class="tesxt-secondary">Haz click en un botón</p>
    <div class="my-5 pb-5">
      <button class="my-btn fs-3" v-for="(item,index) in buttons" :key="index"
        :class="{'bg-primary': index==0,'bg-warning mx-3': index==1,'bg-success': index==2,'bg-secondary mx-3': index==3,'bg-info': index==4,}"
        v-on:click="selectedNum($event)">{{item}}</button>
    </div>
    <p class="text-secondary my-p">{{num}}</p>
  </div>
</template>

<script>
  export default {
    name: 'App',
    data() {
      return {
        num: 0,
        buttons: [3, 5, 8, 10, 20],
        timer: null
      }
    },
    methods: {
      showRemaining() {
        this.num--;
        if (this.num == 0)
          clearInterval(this.timer);
      },
      selectedNum(event) {
        clearInterval(this.timer); //para click de btn seguidos
        this.num = event.currentTarget.innerText;
        this.timer = setInterval(this.showRemaining, 1000);
        this.timer();
      },
    }
  }
</script>

<style scoped>
  .my-btn {
    width: 80px;
    height: 80px;
    border: 1px solid rgb(39, 38, 38);
    border-radius: 5%;
    color: white;
  }

  .my-p {
    width: 150px;
    height: 150px;
    border: 2px solid rgb(39, 38, 38);
    border-radius: 5%;
    font-size: 4rem;
    margin: auto;
    display: flex;
    justify-content: center;
    align-items: center;
  }
</style>