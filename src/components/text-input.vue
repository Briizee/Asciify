<template>
  <div>
    <v-text-field
      color="purple"
      v-model="textInput"
      label="Input text here"
      maxlength="5"
      clearable
      outlined
    ></v-text-field>
  </div>
</template>

<script>
import { Component, Vue, Watch } from 'vue-property-decorator';

@Component({})
export default class TextInput extends Vue {
textInput= '';

@Watch('textInput')
watchTextInput(val) {
  this.$emit('text-updated', val);
}
}
</script>

<style>

</style>
