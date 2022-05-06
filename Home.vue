<script lang='ts' setup>
import { ref } from 'vue'
  const userId = ref(1);
  const zag = ref('Wikipedia')
  const centerBlokArray = ref([
      "Вики по игре  minecraft...",
      "Minecraft — видеоигра в жанре «песочница», написанная на Java, C++, Objective-C и на XNA. Игру изначально создал Маркус «Notch» Перссон, а сейчас её поддержкой занимаются Mojang Studios, управляемые Microsoft Studios.",
      "Minecraft нацелена на предоставление игроку свободы исследовать динамически генерируемую карту, взаимодействовать с ней и изменять её.",
  ])
  const rightBlokArray = ref([' В другие возможности игры входят построение схем из красного камня для логических вычислений и взаимодействия с находящимися на расстоянии объектами, вагонетки и рельсы, а также таинственный подземный мир, называющийся Нижним миром.'])
  const leftBlokArray = ref(['В конце концов, существует совершенно необязательная цель игры — путешествие в измерение под названием Край и победа над драконом Края.'])
</script>
<template>
  <h2 class="zagSite">{{zag}}</h2>
      <img src="src/assets/logoMine.png" class="logoImg">
      <img src="src/assets/mineScrin.jpeg" class="logoImg">
      <img src="src/assets/mineHelloWorld.jpeg" class="logoImg">
      <div class="centerBlok fixUp">
        <p v-for="item of centerBlokArray">{{item}}</p>
      </div>
      <div class="leftBlok">
        <p v-for="item of rightBlokArray">{{item}}</p>
      </div>
      <div class="leftBlok">
        <p v-for="item of leftBlokArray">{{item}}</p>
      </div>
</template>