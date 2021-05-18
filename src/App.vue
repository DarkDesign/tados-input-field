<template>
  <div id="app">
    <div class="inputList">
      <div class="inputList__item">
        <p>Нет поддержки Safari и прочих интернет эксплореров.</p>
      </div>
      <div class="inputList__item">
        <input-filed
            v-model="value"
            :label="`Label`"
        ></input-filed>
      </div>
      <div class="inputList__item">
        <input-filed
            v-model="value"
            :label="`Label`"
            :required="true"
        ></input-filed>
      </div>
      <div class="inputList__item">
        <input-filed
            v-model="value"
            :label="`Label`"
        ></input-filed>
      </div>
      <div class="inputList__item">
        <input-filed
            :value="'ValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValue'"
            :label="`Label`"
        ></input-filed>
      </div>
    </div>

  </div>
</template>

<script>

import InputFiled from "./components/input-filed";
export default {
  name: 'App',
  components: {InputFiled},
  data:function (){
    return {
      value: ''
    }
  }
}
</script>

<style scoped lang="scss">
.inputList{
  width: 70%;
  display: flex;
  flex-direction: column;
  gap: 10px;
  &__item{
    padding: 0 10px;
  }
}
</style>
