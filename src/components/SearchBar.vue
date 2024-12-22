<template>
  <div class="search-box">
    <input type="text" placeholder="검색어 입력" @keyup.enter="movieSearch"
          v-model="inputText"><button type="button" @click="movieSearch">검색</button>
  </div>
</template>

<script>
import { ref, watch} from "vue";

export default {
  name: "SearchBar"
  ,emits : {
    searchVal : {
      default: ''
      ,type:String
    }
  },

  setup(props,{emit}) {
    const inputText = ref('');

    const data = watch(inputText,(currVal, oldVal)=>{
      console.log(currVal, oldVal);
    })

    const movieSearch = ()=>{
      emit('movieSearch',inputText.value);
    }


    return {
      inputText,
      movieSearch,
      data
    }
  }

}
</script>

<style>
.search-box{
  padding: 10px;
  display: flex;
  justify-content: center;
}
.search-box input{
  padding: 5px 10px;
}
.search-box button{
  margin:0;
}
</style>