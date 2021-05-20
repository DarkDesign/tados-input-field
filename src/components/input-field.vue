<template>
  <div class="input-field">
    <input type="text" class="input"
           :class="{'input-nonempty': value.length > 0, 'input-error': error}"
           :value="value"
           @input="$emit('input', $event.target.value)"
           :id="`input${_uid}`"
           :required="required"
    >
    <label :for="`input${_uid}`" v-text="label"></label>
    <div class="error" v-if="error">
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
</template>

<script>
export default {
  name: "input-field",
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
    value:function (newValue, oldValue) {
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
$colors:(
  value: #ffffff,
  label: #9d9daf,
  primary: #848595,
  secondary: #6b6c7b,
  focus: #006ac7,
  error: #e84640
);
.input-field {
  position: relative;
  width: 100%;
  *{
    transition: all .3s;
    font-size: 16px;
  }
  .input {
    width: 100%;
    height: 48px;
    outline: none;
    padding: 18px 16px 6px 16px;
    border-top-left-radius: 4px;
    border-top-right-radius: 4px;
    text-overflow: ellipsis;
    background-color: rgba(map-get($colors, primary), 0.15);
    box-shadow: inset 0 -1px 0 0 map-get($colors, secondary);
    color: map-get($colors, value);
    &:focus {
      box-shadow: inset 0 -2px 0 0 map-get($colors, focus);
      & + label {
        transform: scale(0.7) translate(-10px, -16px);
      }
    }
    &:hover {
      background-color: rgba(map-get($colors, primary), 0.25);
      &:not(:focus):not(.input-error) {
        box-shadow: inset 0 -1px 0 0 map-get($colors, primary);
      }
    }
    &-nonempty + label {
      transform: scale(0.7) translate(-10px, -16px);
    }
    &-error {
      box-shadow: inset 0 -1px 0 0 map-get($colors, error);
    }
  }
  label {
    position: absolute;
    top: 12px;
    left: 16px;
    line-height: 1.5;
    user-select: none;
    cursor: text;
    color: map-get($colors, label);
  }
  .error {
    margin-top: 6px;
    display: flex;
    gap: 4px;
    align-content: center;
    color: map-get($colors, error);
    &__message {
      font-size: 13px;
    }
  }
}
</style>