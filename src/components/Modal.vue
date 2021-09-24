<template>
  <div class="backdrop" @click.self="closeModal">
      <div class="modal" :class="{success:theme==='success', danger:theme1==='delete'}">
        <!--<h1>{{header}}</h1>
          <p>{{content}}</p>-->
          <slot/>
      </div>
      
  </div>
</template>

<script>
export default {
    //receive props data from parent
    props:['header', 'content', 'theme', 'theme1'],
    methods:{
        //event emit child to parent prepare data
        closeModal(){
           this.$emit("close")
        }
    }
}
</script>

<style scoped>
    .backdrop{
        position: fixed;
        top: 0;
        background: rgba(0,0,0,0.5);
        width: 100%;
        height: 100%;
    }
    .modal{
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background-color: #fff;
        border-radius: 10px;
    }
    p{
        font-style: normal;
    }
    .success{
        background-color: rgb(50, 207, 10);
        color:#ffff;
    }
    .danger{
        background-color: crimson;
        color: #fff;
    }
</style>