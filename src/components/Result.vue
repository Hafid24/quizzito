<template>
  <div class="flex flex-column align-center">
    <div class="flex ">
      <span class="text-gray">النتيجة النهائية</span>
    </div>
    <div class="flex ">
      <h1 class="big-title mt-1">{{result}}</h1>
    </div>
    <div class="flex flex-row" >
      <div class="flex save-btn">
            حفظ
      </div>
      <div class="flex">
        <input name="name" class="input" placeholder="اكتب اسمك هنا" />
      </div>
    </div>
  </div>
  </template>

<script>

export default {
  name: 'result',
  props: ['result'],
}
</script>

<style>
.align-center {
  align-items: center;
}

.flex {
  display: flex
}
.flex-column  { 
  flex-direction: column 
}
.flex-row { 
  flex-direction: row 
}

.big-title {
  font-family: "Product Sans", "Cairo", Helvetica, Arial, serif;
  line-height: 1.5;
}

.save-btn {
  background-image: linear-gradient(90deg, #F9A03A, #ff2dca);
  border: 0;
  padding: 15px 40px;
  margin-right: 15px;
  color: #fff;
  border-radius: 40px;
  align-items: center;
  color: #fff;
  transition: all 0.3s ease;
}

.input {
  border-radius: 30px;
  padding: 5px 20px;
  height: 55px;
  border-color: #ebebed;
  box-shadow: 0 0 5px rgba(38, 38, 76, 0.05);
  border: 1px solid #ced4da;
  text-align: right;
}
.input:focus {
  outline-offset: -2px;
  color: #495057;
  background-color: #fff;
  border-color: #80bdff;
  outline: 0;
  box-shadow: 0 0 0 0.2rem rgba(0,123,255,.25);
}
.save-btn:hover{
  cursor: pointer;
  background-image: linear-gradient(90deg, #ff2dca,#F9A03A);
}
.text-center {
  text-align: center;
}

.text-gray {
  color: #a7a2ce !important;
  padding-bottom: 0.5rem;
}
.mt-1 {
  margin-top: 0.24rem;
}
</style>
