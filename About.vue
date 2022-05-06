<script lang='ts' setup>
import { ref } from 'vue'
import { useStore } from '../store'
  const store =useStore();
  const userId = ref(1);
  const zag = ref('Железный слиток')
  const centerBlokArray = ref([
      "Железный слиток (англ. Iron Ingot) — слиток универсального металла, широко используемый в крафте.",
      "Железный слиток выпадает при смерти железных големов,.",
      "Чары «Добыча» не увеличивают количество выпадающих слитков.",
      "Добывается посредством выплавки железной руды или необработанного железа",
  ])
  const rightBlokArray = ref(['Железные слитки могут быть найдены в сундуках сокровищниц и лесных особняков (с шансом в 18,8 %) в количестве 1-4; в крепостях (с шансом в 23,4 % в алтарных комнатах и 35,6 % в хранилищах), в адских крепостях (с шансом в 19,2 %), в пустынных храмах (с шансом в 18,2 %), в кузницах деревень (с шансом в 46,1 %), в храмах джунглей (с шансом в 44,5 %), в вагонетках с сундуками в заброшенных шахтах (с шансом в 32 %) в количестве 1-5; в городах Края (с шансом в 39,4 %) в количестве 4-8.'])
  const leftBlokArray = ref(['Железная руда (англ. Iron Ore) — металлическая руда, выплавляемые из которой слитки являются часто используемым материалом для крафта многих предметов. Глубинная железная руда (англ. Deepslate Iron Ore) — это вариант железной руды, генерирующийся ниже Y = 0.'])
</script>

<template>
  <h2 class="zagSite">О предмете  </h2>
      <router-link :to="`/recepe/1`" class="clear"><h3 class="zagPlot">{{zag}}</h3></router-link>
      <img src="src/assets/iron.png"  class="imgRecept">
      <div class="text centerReceptBlok">
        <p v-for="item of centerBlokArray">{{item}}</p>
      </div>
      <div class="text leftReceptBlok">
        <p v-for="item of leftBlokArray">{{item}}</p>
      </div>
      <div class="text rightReceptBlok">
        <p v-for="item of rightBlokArray">{{item}}</p>
      </div>
</template>