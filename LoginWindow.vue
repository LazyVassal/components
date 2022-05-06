<script lang='ts' setup>
  import { nextTick, ref } from 'vue'
  import { useStore } from '../store'
  const id = 1, pos = 1;
  const textBoxNew = ref([
      {id: 1, sod: '', position: 1},
  ])
  const recepts = ref([
      {name: 'Название', ingred:'Ингредиенты',rec: 'Рецепт', opis: 'Описание'},
      ])
const store =useStore()
  async function getUsers() {
    const url = 'http://192.168.1.31:3000/auth/login';

    let user = {
      username: store.userlog,
      password: store.userpass
    }
    
    let response = await fetch(url , {
      method: 'Post',
      headers: {
        'Content-Type': 'application/json;charset=utf-8'
      },
      body: JSON.stringify(user)
    });
    let result = await response.json();
    console.log(response);
    if (!response.ok){
      console.clear();
      alert('неверные данные');
    } 
    else {
      alert("Добро пожаловать "+user.username);
      store.st =true;
      store.log = false;
      store.token = result.token;
      store.nikLog= user.username;
    }
    console.log(result);
}

  function exitUser(){
    alert('Вы вышли с сайта')
    store.userlog = '';
    store.userpass = '';
    store.st =false;
    store.log = true;
    store.creatSt = false;
  }
  function regestr(){
    store.log = !store.log;
    store.reg = !store.reg;
  }
</script>
<template>
   <div class="loginPage" v-if="store.log">
    <h3 class="logH">Вход</h3>
      <input type="text" name="login" v-model="store.userlog" placeholder="Логин">
      <label for="login">Логин</label>
      <br>
      <input type="password" name="pass" v-model="store.userpass" placeholder="Пароль">
      <label for="pass">Пароль</label>
      <br>
      <button @click="getUsers">Войти</button>
      <button @click="regestr">Зарегестрироваться</button>
    </div>
    <div class="loginPage" v-if="store.reg">
        <h3 class="logH">Регестрация</h3>
      <input type="text" name="nick" placeholder="Ник">
      <label for="nick">Ник</label>
      <input type="text" name="login" placeholder="Логин">
      <label for="login">Логин</label>
      <br>
      <input type="password" name="pass" placeholder="Пароль">
      <label for="pass">Пароль</label>
      <br>
      <button>Зарегестрироваться</button>
      <button @click="regestr">Назад</button>
    </div>
    <div v-if="store.st" class="userState">
        <p>Ник:  {{store.nikLog}}</p>
        <button @click="store.creatSt = !store.creatSt">Написать статью</button><br>
        <button @click="exitUser" v-if="store.st">Выйти</button>
    </div>
    <div class="creatSt" v-if="store.creatSt">
        <input type="text" name="zag" placeholder="Zag" tabindex="1">
            <label for="zag"> - укажите название статьи</label>
        <input type="text"  list="tagsItems" name="tagSt" placeholder="tag" tabindex="2">
            <label for="tagSt"> - выберете тег</label><br>
        <div id="tagsItems" v-for="item of store.treeData.item">
            <input type="checkbox" id="{{item.name}}">
            
            <label for="{{item.name}}">{{item.tag_name}}</label>
        </div>
        <input type="text" name="imgSrc" placeholder="img" tabindex="4">
            <label for="imgSrc"> - Добавьте ссылку на картинку</label><br>

        <span v-for="item of textBoxNew">
                <textarea placeholder="Textbox" v-model="item.sod"></textarea><br>
        </span>
        <button @click="textBoxNew.push({id: ++id, sod: '', position: ++pos},)">Добавить  абзац</button>
        <button @click="pos--; textBoxNew.pop();">Удалить абзац</button>
        <h3>Рецепты</h3>
        <table>
            <span v-for="item of recepts">
                <th><input type="text" v-model="item.name"></th>
                <tr>
                    <td class=""><input type="text" v-model="item.ingred"></td>
                    <td class=""><input type="text" v-model="item.rec"></td>
                    <td class=""><input type="text" v-model="item.opis"></td>
                </tr>
            </span>
        </table>
        <button @click="recepts.push({name: 'Название', ingred:'Ингредиенты',rec: 'Рецепт', opis: 'Описание'},)">Добавить рецепт</button>
          <button @click="recepts.pop()">Удалить рецепт</button><br>
        <button class="creatSt-btn">Создать статью</button>
    </div>
</template>
<style>
.creatSt-btn{
    margin-left: 80%;
}
</style>