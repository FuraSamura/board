<template>
  <vEditPopup
      v-show="isEditPopupVisible && isBackEffect"
      @closeEditPopup="closeEditPopup"
      :class="{'panel-popup-cens': isBackEffect}"
  />
    <div class="task">
      <div class="content" 
        :class="{ 'task-panel': true}" 
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
          <h5 @dblclick="showEditPopup">{{item.title}}</h5>
        </div>
      </div>
    </div>
    
</template>
<script>
import { ref } from 'vue'
import vEditPopup from '../popup/editTaskPopup.vue'

  export default {
    components: {
    vEditPopup
},
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
      },
      methods:{
      showEditPopup(){
        this.isEditPopupVisible = true;
        this.isBackEffect = true;
      },
      closeEditPopup(){
        this.isEditPopupVisible = false;
        this.isBackEffect = false;
      }
    },
    data() {
      return{
        isEditPopupVisible: false,
        isBackEffect: false,
        showContextMenu: false
      }
    }
  }
</script>
<style scoped>
.task
{
  position: static;
  display: table;
  
}
.task-panel
{
    display: table-cell;
    border-radius: 3px;
    position: static;
    width: 1%;
    padding-left: 10px;
    font-family: Andale Mono, monospace;
    font-weight: 500;
}
.task-panel-popup
{
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
.panel-popup-cens
{
  background: #5c5c5ca3;
  width: 100%;
  height: 100%;
}
</style>