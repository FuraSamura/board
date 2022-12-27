<template>
    <div class="v-popup-wrapper">
        <div class="v-popup">
            <div class="_header">
                <h3 :style="{fontFamily: 'Andale Mono, monospace'}">Создать задачу</h3>
                <span>
                    <i 
                    class="material-icons"
                    @click="closePopup"
                    >close</i>
                </span>
            </div>
            <div class="_content">
              <div class="text-field text-field_floating-2">
                <input class="text-field__input" type="name" id="name" name="name" placeholder="Наименование">
                <label class="text-field__label" for="name">Наименование</label>
              </div>
              <div class="text-field text-field_floating-2">
                <input class="text-field__input" type="desc" id="desc" name="desc" placeholder="Описание">
                <label class="text-field__label" for="desc">Описание</label>
              </div>
              <div>
                <label>
                  <input type="file" class="input-file">
                </label>
              </div>
            </div>
            <div class="_footer">
                <button class="btn-editTask" @click="closePopup">Close</button>
                <button class="btn-editTask">Apply</button>
            </div>
            
        </div>
    </div>
</template>
  <script>
  export default {
      methods:{
        closePopup(){
            this.$emit('closePopup');
        }
      }
  }
  </script>
<style>
.v-popup-wrapper
{
    display: flex;
    justify-content: center;
    align-items: center;
    position: fixed;
    right: 0;
    top: 0;
    left: 0;
    bottom: 0;
}
.v-popup 
{
    position: absolute;
    padding: 16px;
    left: 40%;
    top: 50%;
    width: 29%;
    margin-left: -100px;
    margin-top: -75px;
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
    justify-content: center;
    align-items: center;
    margin: 30px;
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
}
.btn-editTask:active 
{
  background:rgb(23, 77, 255);;
}
.btn-editTask:hover 
{
  background:rgb(23, 77, 255);;
  transition: 0.4s;
}
.material-icons
{
    transition: 0.3s;
  border-style: solid;
  padding-left: 15px;
  padding-top: 7px;
  padding-bottom: 7px;
  border: 0ch;
  border-color:black;
  margin-right: 10%;
  cursor: context-menu;
}
.material-icons:active 
{
    transition: 0.3s;
  background:rgb(223, 223, 223);;
}
.material-icons:hover 
{
    background:rgb(228, 228, 228);;
  transition: 0.4s;
}

.text-field__label 
{
  display: block;
  margin-bottom: 0.25rem;
  font-family: Andale Mono, monospace;
}

.text-field__input 
{
  display: block;
  width: 100%;
  height: calc(2.25rem + 2px);
  padding: 0.375rem 0.75rem;
  font-family: inherit;
  font-size: 20px;
  font-weight: 400;
  line-height: 1.5;
  color: #212529;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #bdbdbd;
  border-radius: 0.25rem;
  transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

.text-field__input[type="search"]::-webkit-search-decoration,
.text-field__input[type="search"]::-webkit-search-cancel-button,
.text-field__input[type="search"]::-webkit-search-results-button,
.text-field__input[type="search"]::-webkit-search-results-decoration 
{
  -webkit-appearance: none;
}

.text-field__input::placeholder 
{
  color: #212529;
  opacity: 0.4;
}

.text-field__input:focus 
{
  color: #212529;
  background-color: #fff;
  border-color: #bdbdbd;
  outline: 0;
  box-shadow: 0 0 0 0.2rem rgba(158, 158, 158, 0.25);
}

.text-field__input:disabled,
.text-field__input[readonly] 
{
  background-color: #f5f5f5;
  opacity: 1;
}

    /* with floating label */
.text-field_floating-2 
{
  position: relative;
  display: flex;
  margin-bottom: 20px;
}

.text-field_floating-2 .text-field__input 
{
  height: calc(2.5rem + 2px);
  padding: 0.5rem 0.75rem;
}

.text-field_floating-2 .text-field__label 
{
  position: absolute;
  top: 50%;
  left: 0.3125rem;
  display: flex;
  transform: translateY(-50%);
  pointer-events: none;
  border: none;
  background-color: #fff;
  color: #757575;
  padding-left: 0.5rem;
  padding-right: 0.5rem;
  transition: top 0.1s ease-in-out, scale 0.1s ease-in-out;
}

.text-field_floating-2 .text-field__input::-moz-placeholder 
{
  color: transparent;
}

.text-field_floating-2 .text-field__input::placeholder 
{
  color: transparent;
}

.text-field_floating-2 .text-field__input:focus~.text-field__label,
.text-field_floating-2 .text-field__input:not(:placeholder-shown)~.text-field__label 
{
  top: 0;
  transform: translateY(-50%) scale(0.75);
}

/* Button */
.input-file {
	position: relative;
	display: inline-block;
}
.input-file-btn {
	position: relative;
	display: inline-block;
	cursor: pointer;
	outline: none;
	text-decoration: none;
	font-size: 14px;
	vertical-align: middle;
	color: rgb(255 255 255);
	text-align: center;
	border-radius: 4px;
	background-color: #419152;
	line-height: 22px;
	height: 40px;
	padding: 10px 20px;
	box-sizing: border-box;
	border: none;
	margin: 0;
	transition: background-color 0.2s;
}
.input-file-text {
	padding: 0 10px;
	line-height: 40px;
	display: inline-block;
}
.input-file input[type=file] {
	position: absolute;
	z-index: -1;
	opacity: 0;
	display: block;
	width: 0;
	height: 0;
}
 
/* Focus */
.input-file input[type=file]:focus + .input-file-btn {
	box-shadow: 0 0 0 0.2rem rgba(0,123,255,.25);
}
 
/* Hover/active */
.input-file:hover .input-file-btn {
	background-color: #59be6e;
}
.input-file:active .input-file-btn {
	background-color: #2E703A;
}
 
/* Disabled */
.input-file input[type=file]:disabled + .input-file-btn {
	background-color: #eee;
}
</style>