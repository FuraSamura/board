<template>
    <div class="task">
      <div class="content" 
        :class="{ 'task-panel': true }" 
        @drop="onDrop($event, category.id)"
        v-for="category in categories"
        :key="category.id"
        :style="{ borderLeft: 'thick solid' + category.color}" 
        @dragover.prevent
        @dragenter.prevent>
        <p>{{ category.title }}</p>
        <div v-for="item in items.filter(x => x.categoryId === category.id)"
          @dragstart="onDragStart($event, item)" 
          :key="item.id" 
          draggable="true" 
          class="draggable">
          <h5>{{item.title}}</h5>

        </div>
      </div>
    </div>
</template>
<script>
import { ref } from 'vue'

  export default {
      setup(){
        const items = ref([
        {
          id: 0,
          title: 'test1',
          categoryId: 0
        },
        {
          id: 1,
          title: 'test2',
          categoryId: 0
        }
      ])
        const categories = ref([
        {
          id: 0,
          title: 'Идеи',
          color: '#ff0000'
        },
        {
          id: 1,
          title: 'В разработке',
          color: '#f9b436'
        },
        {
          id: 2,
          title: 'Сделано',
          color: '#56ffd8'
        },
        {
          id: 3,
          title: 'Завершено',
          color: '#5ff95c'
        }
      ])

        function onDragStart(event, item)
        {
          event.dataTransfer.dropEffect = 'move';
          event.dataTransfer.effectAllowed = 'move';
          event.dataTransfer.setData('itemId', item.id.toString());
        }
        function onDrop(event, categoryId)
        {
          const itemId = parseInt(event.dataTransfer.getData('ItemId'));
          items.value = items.value.map(x=>{
            if(x.id == itemId)
              x.categoryId = categoryId;
            return x;
          })

        }

        return{
          items,
          categories,
          onDragStart,
          onDrop
        }
      }
  }
</script>
<style scoped>
.task
{
  position: absolute;
  display: table;
  
}
.task-panel
{
    background: white;
    display: table-cell;
    border-radius: 3px;
    position: relative;
    width: 1%;
    padding-left: 10px;
    font-family: Andale Mono, monospace;
    font-weight: 500;
}
.content
{
  border-left: thick, solid, var(--color)
}
</style>