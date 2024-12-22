<template>
  <navbar/>

  <searchbar @movieSearch="movieSearch"/>

  <movies :data="data_temp"
          @detail="detail($event)"
          @likes="likes($event)"
  />

  <modal v-if="isModal"
         :selectTitle="selectTitle"
         :isModal="isModal"
         @isModal="isModal=false"/>
</template>

<script>
import libs from "@/assets/scripts/movies";
import navbar from "@/components/Navbar.vue"
import modal from "@/components/Modal.vue"
import movies from "@/components/Movies.vue"
import searchbar from "@/components/SearchBar.vue"

export default {
  name: 'App'
  , components: {
    navbar
    , modal
    , movies
    , searchbar
  }
  , data() {
    return {
      isModal: false
      , selectTitle: ''
      , foods: ['김밥', '순대', '만두']
      , data: libs.data
      , data_temp : libs.data
    }
  }
  , methods: {
    likes(obj) {
      obj.like++;
    }
    , detail(obj) {
      console.log(obj);
      this.isModal = true;
      this.selectTitle = obj.title;
    }
    , closeModal(data) {
      this.isModal = data;
    }
    , movieSearch(data) {
      this.data_temp = this.data.filter((item) => {
          return item.title.includes(data);
      })
    }
  }
  ,mounted() {
    alert(document.querySelector(".search-box"));
  }
  ,created() {
    alert(this.data.length);
  }
  ,unmounted() {
    alert(this.data.length);
  }
}
</script>

<style>

* {
  box-sizing: border-box;
  margin: 0;
}

body {
  max-width: 768px;
  margin: 0 auto;
  padding: 20px;
}

h1, h2, h3 {
  margin-bottom: 1rem;
}

p {
  margin-bottom: 0.5rem;
}

button {
  margin-right: 10px;
  margin-top: 1px;
}

.item {
  width: 100%;
  border: 1px solid #ccc;
  display: flex;
  margin-bottom: 20px;
  padding: 1rem;
}

.item figure {
  width: 30%;
  margin-right: 1rem;
}

.item img {
  width: 100%;
}

.item .info {
  width: 100%;
}

.item button {
  cursor: pointer;
}

.modal {
  background: rgba(0, 0, 0, 0.7);
  position: fixed;
  left: 0;
  top: 0;
  width: 100%;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal .inner {
  background: #fff;
  width: 80%;
  padding: 20px;
  border-radius: 10px;
}
</style>
