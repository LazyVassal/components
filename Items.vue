<script lang='ts' setup>
  import { useStore } from '../store'
  const store =useStore();
   
    
  function getItem(id: string){
    store.getItem = id;
  }
</script>
<template>
  <h2 class="zagSite">Предметы</h2>
      <div class="centerItemBlok" v-for="data of store.data">
      <span v-if="data.item.length">
        <p class="tagItems" >{{data.tag_name}}</p>
        <p class="tagItem" v-for="it of data.item"><router-link to="/about" class="clear"><a @click="getItem(it.id)">{{it.item_name}}</a></router-link></p>
        </span>
      </div>
     
</template>
<style>
.tagItems{
  padding-left: 1%;
  border-bottom: 2px solid;
  text-transform: bold;
  font-weight: bold;
}
.tagItem{
  padding-left: 3%;
}
.centerItemBlok{
  display: inline-block;
  text-align: left;
  padding: 10% 0% 0% -15%;
  margin-left: 7%;
  width:  32vh;
  height: auto;
}
.clear {
  text-decoration: none;
  color: black;
}
</style>
