<template>

  <div class="menu">
    <a v-for="(menuName,i) in menuNames" :key="i"> {{menuName}} </a>
  </div>

  <img alt="Vue logo" src="./assets/logo.png">
  <div v-for="(product,i) in products" :key="i">
    <h4 :style="스타일"> {{ product.name }}</h4>
    <p>{{ product.price }} 만원</p>
    <button @click="() => increase(i)">허위매물신고</button> <span>신고수 : {{product.count}}</span>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      count : 0,
      menuNames : ['Home','Shop','About'],
      prices : [60, 70, 80],
      스타일 : 'color : blue',
      products : [
        {name : '역삼동원룸', price : 60, count : 0},
        {name : '천호동원룸', price : 70, count : 1},
        {name : '마포동원룸', price : 80, count : 2},
      ],
    }
  },
  methods : {
    increase(i){
      this.products[i].count += 1;
    }
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a{
  color: white;
  padding: 10px;
}
</style>
