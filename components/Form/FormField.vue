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
    :class="className"
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
    className: {
      type: String,
      default: ''
    },
    placeholder: {
      type: String,
      default: ''
    }
  }
}
</script>
