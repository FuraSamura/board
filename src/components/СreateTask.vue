<template>

  <v-popup
    v-if="isInfoPopupVisible"
  />

  <div class="d-table w-100">
    <p class="text">Задачи</p>
    <div class="d-table-cell tar">
      <button class="btn" @click="showPopup">Создать</button>
      <example-modal ref="modal"></example-modal>
    </div>
  </div>
</template>
<script>
import vPopup from '../popup/editTask.vue'
export default {
    components:{
      vPopup
    },
    data(){
      return{
        isInfoPopupVisible: false
      }
    },
    methods:{
      showPopup(){
        this.isInfoPopupVisible = true;
      }
    }
}
</script>
<style scoped>
.text
{
  color:rgb(54, 54, 54);
  font-size:25px;
  font-weight:400;
  display:table-cell;
  padding-left: 10%;
  font-family: 'Inter', sans-serif;
}
.btn 
{
  transition: 0.3s;
  color:white;
  font-size: 13px;
  border-radius: 3px;
  background: rgb(74, 116, 253);
  border-style: solid;
  padding-left: 15px;
  padding-right: 15px;
  padding-top: 7px;
  padding-bottom: 7px;
  border: 0ch;
  box-shadow: 0 0 100px;
  border-color:black;
  margin-right: 10%;
}
.btn:active 
{
  background:rgb(23, 77, 255);;
}
.btn:hover 
{
  background:rgb(23, 77, 255);;
  transition: 0.4s;
}

.d-table {
  display:table;
  padding-bottom: 10px;
  padding-top: 20px;
}

.w-100 {
  width: 100%;
}

.tar {
  text-align: right;
}
</style>
