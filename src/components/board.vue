<template>
  <div class="board-grid">
  <v-container fill-height>
      <v-row
      fill-height
      align="center"
      justify="center"
      no-gutters >
          <v-col
          class="row1columns"
          justify="center"
          align="center"
          v-for="n in 3"
          :key="n"
          cols="4"
          >
          <pre>{{ outputText }}</pre>
          </v-col>
      </v-row>
      <v-row
      fill-height
      align="center"
      justify="center"
      no-gutters >
          <v-col
          class="row2columns"
          justify="center"
          align="center"
          v-for="n in 3"
          :key="n"
          cols="4"
          >
          <pre>{{ outputText }}</pre>
          </v-col>
      </v-row>
      <v-row
      fill-height
      align="center"
      justify="center"
      no-gutters >
          <v-col
          class="row3columns"
          justify="center"
          align="center"
          v-for="n in 3"
          :key="n"
          cols="4"
          >
          <pre>{{ outputText }}</pre>
          </v-col>
      </v-row>
  </v-container>
  </div>
</template>

<script lang="ts">
import {
  Component, Vue, Prop, Watch,
} from 'vue-property-decorator';
import figlet, { fonts } from 'figlet';
import * as path from 'path';
import * as fs from 'file-system';
import * as Fonts from '../fontsImports';

@Component({})
export default class Board extends Vue {
  @Prop({ default: 'Standard' }) font!: string

  @Prop({ default: 'Hello' }) text!: string

  outputText = '';

  mounted() {
    const fontsArray = Object.keys(Fonts);

    fontsArray.forEach((key: string) => {
      (figlet as any).parseFont(key, Fonts[key]);
    });
  }

  @Watch('text')
  watchText() {
    this.getAscii();
  }

  @Watch('font')
  watchFont() {
    this.getAscii();
  }

  getAscii() {
    (figlet as any).text(this.text, {
      font: this.font,
      horizontalLayout: 'default',
      verticalLayout: 'default',
      width: 80,
      whitespaceBreak: true,
    }, (err: any, data: any) => {
      this.outputText = data;
    });
  }
}
</script>

<style>
.board-grid {
    height: 100%;
    text-align: center;
    background-color: black;
}

.row1columns:nth-child(1) {
  color:mediumvioletred;
}

.row1columns:nth-child(2) {
  color: greenyellow;
}

.row1columns:nth-child(3) {
  color:mediumvioletred;
}

.row2columns:nth-child(2) {
  color:mediumvioletred;
}

.row2columns:nth-child(1) {
  color: greenyellow;
}

.row2columns:nth-child(3) {
  color: greenyellow;
}

.row3columns:nth-child(1) {
  color:mediumvioletred;
}

.row3columns:nth-child(2) {
  color: greenyellow;
}

.row3columns:nth-child(3) {
  color:mediumvioletred;
}

</style>
