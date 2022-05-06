<script setup lang="ts">
import { ref, computed } from 'vue'
import { useStore } from '../store'
  const store =useStore();

const props = defineProps({
  model: Object
})

const isOpen = ref(false)
const isFolder = computed(() => {
  return props.model?.item?.length
})

function toggle() {
  isOpen.value = !isOpen.value;
}
function getID(id: string){
  store.getItem = id;
  console.log(store.getItem)
}


</script>

<template>
  <li>
    <div
      :class="{ bold: isFolder }"
      @dblclick="toggle"
      @click="getID(model?.id)"
      >
      {{ model?.tag_name }}
      <router-link class="clear" :key="model?.name" :to="`/recepe/${model?.id}`" >
      {{ model?.name }}
      </router-link>

      <span v-if="isFolder">[{{ isOpen ? '-' : '+' }}]</span>
    </div>
    <ul v-show="isOpen" v-if="isFolder">
      <!--
        A component can recursively render itself using its
        "name" option (inferred from filename if using SFC)
      -->
      <TreeItem
        class="item"
        v-for="model in props.model?.item"
        :key="model.tag_name"
        :model="model">
      </TreeItem>
    </ul>
  </li>
</template>