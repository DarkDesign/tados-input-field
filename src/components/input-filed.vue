<template>
  <div class="input-filed">
      <input type="text" class="input"
             :class="{'input-nonempty': value.length > 0, 'input-error': error}"
             :value="value"
             @input="$emit('input', $event.target.value)"
             :id="`input${_uid}`"
             :required="required"
      >
      <label :for="`input${_uid}`" v-text="label"></label>
      <div class="error">
        <div class="error__wrapper" v-if="error">
          <div class="error__icon">
            <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 16 16">
              <g fill="none" fill-rule="evenodd">
                <g fill="#E84640">
                  <path d="M8 0c4.418 0 8 3.582 8 8s-3.582 8-8 8-8-3.582-8-8 3.582-8 8-8zm0 2C4.687 2 2 4.686 2 8c0 3.313 2.687 6 6 6s6-2.687 6-6c0-3.314-2.687-6-6-6zm2.121 2.464l1.414 1.414L9.414 8l2.121 2.121-1.414 1.414L8 9.415l-2.121 2.12-1.414-1.414 2.121-2.12-2.121-2.123 1.414-1.414L8 6.585l2.121-2.12z" transform="translate(0 -2) translate(0 2)"/>
                </g>
              </g>
            </svg>
          </div>
          <div class="error__message" v-text="errorMessage"></div>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  name: "input-filed",
  props:{
    value:{
      type: String,
      default: ''
    },
    label:{
      type: String,
      default: ''
    },
    required:{
      type: Boolean,
      default: false
    },
    errorMessage:{
      type: String,
      default:'Error text'
    }
  },
  data:function (){
    return {
      error: false
    }
  },
  watch:{
    value:function (newValue, oldValue){
      if(this.required) this.error = (oldValue.length > 0 && newValue.length === 0)
    }
  }
}
/**
 * *
 * User: DarkDesign
 * Date: 18.05.2021
 * Time: 21:35
 */
</script>

<style scoped lang="scss">
$color: [
  #ffffff,
  #9d9daf,
  #848595,
  #6b6c7b,
  #006ac7,
  #e84640
];
.input-filed {
  position: relative;
  width: 100%;
  *{
    transition: all .3s;
    font-size: 16px;
    font-family: "OpenSans";
  }
  .input{
    width: 100%;
    height: 48px;
    outline: none;
    padding: 18px 16px 6px 16px;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
    text-overflow: ellipsis;
    background-color: rgba(nth($color, 3), 0.15);
    border-bottom: 1px nth($color, 4) solid;
    color: nth($color, 1);
    &:focus{
      &:not(.input-error){
        border-bottom-color: nth($color, 5);
        box-shadow: 0 1px 0 0 nth($color, 5);
      }
      &+ label {
        transform: scale(0.7) translate(-10px, -16px);
      }
    }
    &:hover:not(:focus){
      background-color: rgba(nth($color, 3), 0.25);
      border-bottom: 1px nth($color, 3) solid;
    }
    &-nonempty + label{
      transform: scale(0.7) translate(-10px, -16px);
    }
    &-error{
      border-bottom: 1px nth($color, 6) solid;
    }
  }
  label{
    position: absolute;
    top: 12px;
    left: 16px;
    line-height: 1.5;
    color: nth($color, 2);
  }
  .error{
    margin-top: 6px;
    min-height: 16px;
    color:nth($color, 6);
    &__wrapper{
      display: flex;
      gap: 4px;
      align-content: center;
    }
    &__message{
      font-size: 13px;
    }
  }
}
</style>