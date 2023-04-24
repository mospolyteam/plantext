<template>
  <select
    :name="name"
    :id="name"
    class="form__input form__input--select"
  >
    <option
      v-for="option in options"
      :value="option.value"
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
      }
    }
}
</script>
