<template>
  <h1>영화정보</h1>
  <div v-for="(obj, idx) in data" :key="idx" class="item" >
    <figure>
      <img :src="`${obj.img_path}`" :alt="obj.title"/>
    </figure>
    <div class="info">
      <h3 class="bg_yellow">{{ obj.title }}</h3>
      <p>개봉: {{ obj.year }}</p>
      <p>장르: {{ obj.category }}</p>
      <button type="button" @click="likes(obj)">좋아요</button>
      <span>{{ obj.like }}</span>
      <p>
        <button type="button" @click="detail(obj)">상세보기</button>
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: "MoviesComponent"
  ,props :{
    data : Object,
  }
  ,emits :{
    detail : Object
    ,likes : Object

  }
  ,setup(props,{emit}) {
    const detail = (obj) =>{
      emit('detail', obj);
    }

    const likes = (obj) =>{
      emit('likes', obj);
    }

    return {
      detail
      ,likes
    }
  }

}
</script>

<style scoped>

</style>