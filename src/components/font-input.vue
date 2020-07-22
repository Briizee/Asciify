<template>
<div class="text-xs-center">
    <v-select
    :items="fontNames"
    label="Font"
    v-model="selectedFont"
    outlined
    color="purple"
    >
    </v-select>
</div>
</template>

<script lang='ts'>
import { Component, Vue, Watch } from 'vue-property-decorator';
import * as Fonts from '../fontsImports';

@Component({})
export default class FontInput extends Vue {
  selectedFont = '';

  @Watch('selectedFont')
  watchSelectedFont(val: string) {
    this.$emit('font-updated', val);
  }

  get fontNames() {
    return Object.keys(Fonts);
  }
}
</script>

<style lang='scss'>

</style>
