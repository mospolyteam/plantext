<template>
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
</template>

<script>
export default {
  name: "FormField",
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
  .form__input {
    background-color: #fff;
    border: 1px solid #1B1917;
    height: 35px;
    padding: 5px 10px;
    min-width: 260px;
    outline: none;
    font-size: 18px;
  }
</style>
