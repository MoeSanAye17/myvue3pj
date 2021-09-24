<template>
<h1>hi</h1>
<!--step3-->
<!--similar to write <Modal/>-->
<!--props parent to child-->
<div v-if="showModal">
  <Modal :header="header" :content="content" :theme="theme" @close="showModal=!showModal">
    <h1>Login success</h1>
    <p>welcome user moe san aye</p>
  </Modal>
</div>
<!--event modifier behind event(.) nae write-->
<button @click="showModal=!showModal">open modal</button><br>

<div v-if="deleteModal">
  <Modal :header="header" :content="content" :theme1="theme1" @close="deleteModal=!deleteModal">
    <h1>Are you sure want to delete?</h1>
    <p>User MoeSanAye</p>
    <p>Thanks, User.</p>
  </Modal>
</div>
<!--event modifier behind event(.) nae write-->
<button @click="deleteModal=!deleteModal">delete modal</button>
</template>

<script>
//step1 do import
import Modal from './components/Modal.vue'
export default {
  data(){
    return{
      header:"Login success",
      content:"welcome user Moe San Aye",
      theme:"success",
      theme1:"delete",
      showModal:false,
      deleteModal:false
    }
  },
  //step2 register
  components:{
    //similar write(Modal)
    Modal:Modal
  }

}
</script>

<style scoped>
    /* h1{
        color: #3e3f;
      } */
      button{ 
        margin: 5px;
      }
</style>