<template>
  <div>
    <div>
      <h1>유튜브 링크를 입력하고 변환 버튼을 클릭하세요.</h1>
    </div>
    <div class="div-link">
      <form @submit.prevent="sendLink">
        <input type="text" v-model="link" class="input-link">&nbsp;
        <button type="submit" class="btn-link">변환</button>
      </form>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    data(){
      return {
        link: '',
      }
    },
    methods: {
      sendLink(){
        axios.get('http://localhost:8090/api/conversion', {
          params: {link: this.link}
        })
        .then(response => {
          console.log(response.data);
        })
        .catch(error =>{
          console.log(error);
        })
      }
    }
  }
</script>

<style>
  .div-link{
    width: 100%;
  }
  .input-link{
    width: 500px
  }
  .button-link{
    width: 70px
  }
  @media screen and (max-width: 620px){
    .input-link{
      width: 70%
    }
    .button-link{
      width: 20%
    }
  }
  @media screen and (max-width: 218px){
    .input-link{
      width: 60%
    }
    .button-link{
      width: 10%
    }
  }
  @media screen and (max-width: 167px){
    .input-link{
      width: 50%
    }
    .button-link{
      width: 10%
    }
  }
</style>
