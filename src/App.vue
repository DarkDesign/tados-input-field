<template>
  <div id="app">
    <div class="inputList">
      <div class="inputList__item">
        <input-field
            v-model="value"
            :label="`Label`"
        ></input-field>
      </div>
      <div class="inputList__item">
        <input-field
            v-model="value"
            :label="`Label`"
            :required="true"
        ></input-field>
      </div>
      <div class="inputList__item">
        <input-field
            v-model="value"
            :label="`Label`"
        ></input-field>
      </div>
      <div class="inputList__item">
        <input-field
            :value="'ValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValueValue'"
            :label="`Label`"
        ></input-field>
      </div>
    </div>

  </div>
</template>

<script>

import InputField from "./components/input-field";
export default {
  name: 'App',
  components: {InputField},
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
