<template>
  <div class="form__input-container">
    <slot name="icon" />
    <input
      @input="$emit('input', $event.target.value)"
      :type="type"
      :name="name"
      :id="name"
      :required="required"
      :value="value"
      :placeholder="placeholder"
      class="form__input"
    >
  </div>
</template>

<script>
import Article from '../Article/Article.vue'
export default {
  components: { Article },
  name: "FormInput",
  emits: ['update:modelValue'],
  props: {
    type: {
      type: String,
      default: 'text'
    },
    name: {
      type: String,
      required: true
    },
    required: {
      type: Boolean,
      default: false
    },
    value: {
      type: [String, Number, Boolean],
      required: true
    },
    placeholder: {
      type: String,
      default: ''
    }
  }
}
</script>

<style>
  .form__input-container {
    display: flex;
    border: 1px solid #1B1917;
    background-color: #fff;
  }
  .form__input {
    border: none;
    height: 35px;
    padding: 5px 10px;
    min-width: 260px;
    width: 100%;
    outline: none;
    font-size: 18px;
  }
  .form__input-container > svg {
    margin: auto;
    margin-left: 10px;
  }
</style>
