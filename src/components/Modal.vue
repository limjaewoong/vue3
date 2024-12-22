<template>
  <div class="modal" v-if="isModal">
    <div class="inner">
      <h3>Detail1</h3>
      <p>영화 상세정보 <span>{{selectTitle}}</span></p>
      <button type="button" @click="$emit('isModal',false)">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name : "ModalComponent"
  ,props : {
    isModal : {
      default : false
    }
    ,selectTitle : String,
  }
  ,emits :{
    isModal : false
  }
  ,setup(props,{emit}) {
    const closeModal = () => {
      emit('isModal', false);
    }

    return {
      closeModal
    }
  }
}
</script>

<style scoped>

</style>