<script setup>
  import q from '../db/questions.json'
  import {ref, watch} from 'vue'
  import Card from '../components/Card.vue'
  

  const search = ref('')
  const quizes = ref(q)

  watch(search, () => {
    quizes.value = q.filter(quiz => quiz.name.toLowerCase().includes(search.value.toLowerCase()))
  })

</script>

<template>
  <div>
    <header>
      <h1>Quizes</h1>
      <input type="text" name="search" id="search" v-model.trim="search" placeholder="Search...">
    </header>
    <div class="options-container">
      
      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz"/>
      <!-- <div v-for="quiz in quizes" :key="quiz.id" class="card">
        <img :src="quiz.img" alt="">
        <div class="card-text">
          <h2>{{quiz.name}}</h2>
          <p>{{quiz.questions.length}} Questions</p>
        </div>
      </div> -->
    </div>
  </div>
</template>

<style scoped>
  header{
    display: flex;
    margin-top: 30px;
    margin-bottom: 10px;
    align-items: center;
    justify-content: space-between;
  }
  header h1{
    font-weight: bold;
    margin-right: 30px;
  }
  header input{
    border: none;
    background-color: rgba(128,128,128,0.1);
    padding: 10px;
    border-radius: 5px;
  }
  .options-container{
    display: flex;
    flex-wrap:wrap;
    margin-top: 40px;
  }
  @media(max-width:500px){
    header{
      flex-direction: column;
    }
    .options-container{
      flex-direction: column;
    }
  }
 
</style>