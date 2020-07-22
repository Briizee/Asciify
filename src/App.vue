<template>
<v-app>
  <div id="app">
    <!-- <pre class="ascii">{{text}}</pre> -->
    <input-dialog @text="getText($event)" @font="getFont($event)"></input-dialog>
    <board v-bind:font="font" v-bind:text="text"/>
  </div>
</v-app>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import figlet, { fonts } from 'figlet';
import * as Fonts from './fontsImports';
import InputDialog from './components/input-dialog.vue';
import Board from './components/board.vue';

@Component({
  components: {
    InputDialog,
    Board,
  },
})
export default class App extends Vue {
  text = ''

  font = ''

  getText(event: string) {
    this.text = event;
  }

  getFont(event: string) {
    this.font = event;
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  height: 100%;
}

input-dialog {
  position: fixed;
  top: 0px;
  left: 0px;
}

.ascii {
  color: magenta;
}
</style>
