<script setup>
import { ref } from 'vue'

const itemsLeft = [
  {
    "id": 1,
    "name": "Shoes 1"
  },
  {
    "id": 2,
    "name": "Shoes 2"
  },
  {
    "id": 3,
    "name": "Shoes 3"
  },
  {
    "id": 4,
    "name": "Shoes 4"
  },
  {
    "id": 5,
    "name": "T-shirt 1"
  },
  {
    "id": 6,
    "name": "T-shirt 2"
  },
  {
    "id": 7,
    "name": "T-shirt 3"
  },
  {
    "id": 8,
    "name": "T-shirt 4"
  }
]

const itemsRight = [
  {
    "id": 11,
    "name": "Jacket 1"
  },
  {
    "id": 12,
    "name": "Jacket 2"
  },
  {
    "id": 13,
    "name": "Jacket 3"
  },
  {
    "id": 14,
    "name": "Jacket 4"
  },
  {
    "id": 15,
    "name": "Hoodie 1"
  },
  {
    "id": 16,
    "name": "Hoodie 2"
  },
  {
    "id": 17,
    "name": "Hoodie 3"
  },
  {
    "id": 18,
    "name": "Hoodie 4"
  }
]

const itemsLeftSelected = ref([])

const isLeftSelected = id => itemsLeftSelected.value.some(i => i.id === id)

const itemRightSelected = ref(null)

const isRightSelected = id => itemRightSelected.value?.id === id

const handleSelectLeft = (item) => {
  if (isLeftSelected(item.id)) {
    itemsLeftSelected.value = itemsLeftSelected.value.filter(i => i.id !== item.id)
  } else {
    itemsLeftSelected.value.push(item)
  }
}

const handleSelectRight = (item) => {
  itemRightSelected.value = item
}
</script>

<template>
  <div class="test-page">
    <div class="selected-items">
      <div class="items-block selected-block">
        <div v-for="item in itemsLeftSelected" class="item">
          {{ item.name }}
        </div>
      </div>
      <div class="items-block selected-block flex-center">
        {{itemRightSelected?.name}}
      </div>
    </div>
    <div class="source-items">
      <div class="items-block">
        <div
            v-for="item in itemsLeft"
            :key="item.id"
            @click="handleSelectLeft(item)"
            class="item item-source"
            :class="{ 'selected': isLeftSelected(item.id) }"
        >
          {{ item.name }}
        </div>
      </div>
      <div class="items-block">
        <div
            v-for="item in itemsRight"
            :key="item.id"
            @click="handleSelectRight(item)"
            class="item item-source"
            :class="{ 'selected': isRightSelected(item.id) }"
            >
          {{ item.name }}
        </div>
      </div>
    </div>
  </div>
</template>
