<template>
  <select
    @input="$emit('input', $event.target.value)"
    :name="name"
    :id="name"
    class="form__input form__input--select"
  >
    <option disabled selected>{{ placeholder }}</option>
    <option
      v-for="option in options"
      :value="option.value"
      :selected="option.value===value"
    >
      {{ option.text }}
    </option>
  </select>
</template>

<script>
export default {
    name: "FormSelect",
    props: {
      options: {
        type: Array,
        default: []
      },
      name: {
        type: String,
        required: true
      },
      value: {
        type: [String, Number, Boolean],
        required: true
      },
      current: {
        type: String,
        default: ''
      },
      placeholder: {
        type: String,
        default: 'Выберите вариант'
      }
    }
}
</script>

<style>

</style>
