<template>
    <div class="dialog">
      <v-dialog
        v-model="dialog"
        width="500"
      >
      <template v-slot:activator="{ on, attrs }">
        <v-btn
          color="purple"
          dark
          v-bind="attrs"
          v-on="on"
        >
          Create
        </v-btn>
      </template>
      <v-card>
        <v-card-title>
            Create ASCII text
        </v-card-title>
        <text-input @text-updated="text=$event" class="card-item-text"/>
        <font-input @font-updated="font=$event" class="card-item-font"/>
      </v-card>
      </v-dialog>
    </div>
</template>

<script lang='ts'>
import { Component, Vue, Watch } from 'vue-property-decorator';
import FontInput from './font-input.vue';
import TextInput from './text-input.vue';

@Component({
  components: {
    FontInput,
    TextInput,
  },
})
export default class InputDialog extends Vue {
  text = '';

  font = '';

  dialog = false;

  mounted() {
    console.log('mounted');
  }

  @Watch('text')
  watchText(val: string) {
    this.$emit('text', val);
  }

  @Watch('font')
  watchFont(val: string) {
    this.$emit('font', val);
  }
}
</script>

<style lang='scss'>
.card-item-text {
    padding: 0px 16px;
}
.card-item-font {
    padding: 0px 16px;
}
.dialog {
  display: flex;
  align-items: flex-start;
  justify-content: flex-start;
  position: absolute;
}
</style>
