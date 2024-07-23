<template>
  <section>
    <base-card>
      <h2>Submitted Data</h2>
      <div>
        <base-button @click="loadData">Load Submitted Data</base-button>
      </div>
      <p v-if="isLoading">Loading...</p>
      <p v-else-if="!isLoading && error">{{ error }}</p>
      <p v-else-if="!isLoading && (!results || results.lenght === 0)">No stored Data Found</p>
      <ul v-else>
        <survey-result
          v-for="result in results"
          :key="result.id"
          :name="result.name"
          :email="result.email"
          :club="result.club"
        ></survey-result>
      </ul>
    </base-card>
  </section>
</template>

<script>
import SurveyResult from './SurveyResult.vue';

export default {
  components: {
    SurveyResult,
  },
  data(){
    return{
      results:[],
      isLoading:false
    }
  },
  methods:{
    loadData(){
      this.isLoading =true;
      this.error= null;
      fetch('https://test-mode-1be41-default-rtdb.firebaseio.com/surveys.json')
      .then((response) =>{
        if(response.ok){
         return response.json();
        }
      }).then((data)=>{
        this.isLoading =false;
        const results =[];
        for (const id in data){
          results.push({
            id:id,
            name:data[id].name,
            club: data[id].club,
            email: data[id].email
          });
        }
        this.results = results;
      })
      .catch((error)=>{
        console.log(error);
        this.isLoading = false;
        this.error ='Failed to fetch data -please try again later.';
      });
        
   }
  },
}
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}

</style>