<template>
    <div class="v-popup">
        <div class="_header">
            <span>Popup name</span>
            <span>
                <i class="material-icons">close</i>
            </span>
        </div>
        <div class="_content">
            <slot></slot>
        </div>
        <div class="_footer">
            <button class="btn-editTask">Close</button>
        </div>
    </div>
</template>
  <script>
  export default {
      
  }
  </script>
<style>
.v-popup
{
    position: fixed;
    padding: 16px;
    top: 50px;
    width: 400px;
    box-shadow: 0 0 17px 0 #e7e7e7;
    background: #ffffff;
    
}
.v-popup ._header
{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.v-popup ._footer
{
    display: flex;
    justify-content: space-between;
    align-items: center;
}
.v-popup ._content
{
    display: flex;
    justify-content: center;
    align-items: center;
}
.btn-editTask
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
</style>