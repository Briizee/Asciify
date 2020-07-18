<template>
  <div id="app">
    <pre class="ascii">{{text}}</pre>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import figlet, { fonts } from 'figlet';
import * as Fonts from './fontsImports';

@Component({})
export default class App extends Vue {
  text = ''
  font = ''

  mounted() {
    this.fetchList();

    (figlet as any).parseFont('Standard', `${Fonts.Standard}`);

    (figlet as any).text('oh hi binnit', {
      font: 'Standard',
      horizontalLayout: 'default',
      verticalLayout: 'default',
      width: 80,
      whitespaceBreak: true,
    }, (err: any, data: any) => {
      this.text = data;
      console.log(this.text, 'text');
    });
  }

  fetchList() {
    return Object.keys(Fonts);
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
  margin-top: 60px;
}

.ascii {
  color: magenta;
}
</style>
