<script lang='ts' setup>
import { ref, watch } from 'vue'
import { useStore } from '../store'
  const store =useStore();
 async function loadRecepes() {
let url = `http://192.168.1.31:3000/items/${store.getItem}`;
let response = await fetch(url , {
      method: 'GET',
      headers: {
        'Content-Type': 'application/json;charset=utf-8',
        'Authorization': `Bearer ${store.token}`
      },
    });
    let result = await response.json();
    console.log(result);
    store.dataRecepts = result
 }
 loadRecepes();
</script>
<template>
  <h2 class="zagSite">Рецепт {{ $route.params.id }}</h2>
      <p class="centerReceptsBlok">{{store.dataRecepts.item_name}}</p>
      <table v-for="item of store.dataRecepts.recipes" class="stTable">
        <th>{{item.recipe_name}}</th>
        <tr>
          <td class="stold1">Где сделано:</td><td>Материалы:</td>
        </tr>
        <tr>
          <td class="stolb1">{{item.where_made}}</td><td class="stolb2">{{item.materials}}</td>
        </tr>
      </table>
</template>

<style>
.stTable{
  margin-left: 15%;
}
.stTable th{
  background-color: green;
  color: #fff;
}
.stTable td{
  line-height: 4.2ch;
}
.stolb1{
  width: 250px;
  min-width: 10%;
}
.stolb2{
  width: 300px;
  min-width: 15%;
}
</style>