<template>

  <div class="black-bg" v-if="modalStatus == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용임</p>
      <button  @click="modalStatus = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="(menuName,i) in menuNames" :key="i"> {{menuName}} </a>
  </div>

  <div v-for="(oneroom,i) in onerooms" :key="i">
    <img :src='oneroom.image' class="room-img">
    <h4 :style="스타일" @click="modalStatus = true"> {{ oneroom.title }}</h4>
    <p>{{ oneroom.price }} 만원</p>
    <p>{{ oneroom.content }} 만원</p>
  </div>
</template>

<script>
// 동적인 ui 만드는법:
//1. ui의 현재상태를 데이터로 저장해둠
//2. 데이터에 따라 ui가 어떻게보일지 작성

import oneroomData from './assets/oneroom.js';

export default {
  name: 'App',
  data(){
    return {
      onerooms: oneroomData,
      modalStatus: false,
      count : 0,
      menuNames : ['Home','Shop','About'],
      prices : [60, 70, 80],
      스타일 : 'color : blue',
      products : [
        {name : '역삼동원룸', price : 60, count : 0, img :'./public/room0.jpg'},
        {name : '천호동원룸', price : 70, count : 1, img :'./public/room0.jpg'},
        {name : '마포동원룸', price : 80, count : 2, img :'./public/room0.jpg'},
      ],
    }
  },
  methods : {
    increase(i){
      this.products[i].count += 1;
    },
  },
  components: {
  }
}
</script>

<style>
body{
  margin: 0;
}

div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; /* 전체를 감싸줌 */
  padding: 20px;
}
.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}

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
