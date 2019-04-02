<template>
  <div :class="$style.sections">
    <div v-for="section in colorSections">
      <vue-headline level="4">{{ section.name.toUpperCase() }}</vue-headline>
      <div :class="$style.palette">
        <div v-for="color in section.colors" :style="{ background: color.hex }">
          <span>{{ color.name }} ({{ color.hex }})</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import VueHeadline from '@/app/shared/components/VueHeadline/VueHeadline.vue';

export default {
  name: 'ColorPalette',
  components: { VueHeadline },
  computed: {
    colorSections() {
      const sections: any = {};
      const arr: any[] = [];

      Object.keys(this.$style).forEach((key: string) => {
        const split = key.split('-');
        const section = split.shift();
        const name = split.join('-');
        const hex = this.$style[key];

        if (!sections[section]) {
          sections[section] = [];
        }

        sections[section].push({ name, hex });
      });

      Object.keys(sections).forEach((key: string) => {
        if (['sections', 'palette'].indexOf(key) === -1) {
          arr.push({ name: key, colors: sections[key] });
        }
      });

      return arr;
    },
  },
};
</script>

<style lang="scss" module>
@import '~@/app/shared/design-system';

.sections {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: $space-20;
}

.palette {
  display: grid;
  grid-template-rows: 1fr;

  div {
    display: flex;
    justify-content: center;
    align-items: center;

    span {
      background: inherit;
      background-clip: text;
      color: transparent;
      filter: invert(1) grayscale(1) unquote('contrast(100)');
    }
  }
}

:export {
  coral-coral-50: palette-color-level('coral', 50);
  coral-coral-100: palette-color-level('coral', 100);
  coral-coral-200: palette-color-level('coral', 200);
  coral-coral-300: palette-color-level('coral', 300);
  coral-coral-400: palette-color-level('coral', 400);
  coral-coral-500: palette-color-level('coral', 500);
  coral-coral-600: palette-color-level('coral', 600);
  coral-coral-700: palette-color-level('coral', 700);
  coral-coral-800: palette-color-level('coral', 800);
  coral-coral-900: palette-color-level('coral', 900);

  blue-blue-50: palette-color-level('blue', 50);
  blue-blue-100: palette-color-level('blue', 100);
  blue-blue-200: palette-color-level('blue', 200);
  blue-blue-300: palette-color-level('blue', 300);
  blue-blue-400: palette-color-level('blue', 400);
  blue-blue-500: palette-color-level('blue', 500);
  blue-blue-600: palette-color-level('blue', 600);
  blue-blue-700: palette-color-level('blue', 700);
  blue-blue-800: palette-color-level('blue', 800);
  blue-blue-900: palette-color-level('blue', 900);

  green-green-50: palette-color-level('green', 50);
  green-green-100: palette-color-level('green', 100);
  green-green-200: palette-color-level('green', 200);
  green-green-300: palette-color-level('green', 300);
  green-green-400: palette-color-level('green', 400);
  green-green-500: palette-color-level('green', 500);
  green-green-600: palette-color-level('green', 600);
  green-green-700: palette-color-level('green', 700);
  green-green-800: palette-color-level('green', 800);
  green-green-900: palette-color-level('green', 900);

  yellow-yellow-50: palette-color-level('yellow', 50);
  yellow-yellow-100: palette-color-level('yellow', 100);
  yellow-yellow-200: palette-color-level('yellow', 200);
  yellow-yellow-300: palette-color-level('yellow', 300);
  yellow-yellow-400: palette-color-level('yellow', 400);
  yellow-yellow-500: palette-color-level('yellow', 500);
  yellow-yellow-600: palette-color-level('yellow', 600);
  yellow-yellow-700: palette-color-level('yellow', 700);
  yellow-yellow-800: palette-color-level('yellow', 800);
  yellow-yellow-900: palette-color-level('yellow', 900);

  red-red-50: palette-color-level('red', 50);
  red-red-100: palette-color-level('red', 100);
  red-red-200: palette-color-level('red', 200);
  red-red-300: palette-color-level('red', 300);
  red-red-400: palette-color-level('red', 400);
  red-red-500: palette-color-level('red', 500);
  red-red-600: palette-color-level('red', 600);
  red-red-700: palette-color-level('red', 700);
  red-red-800: palette-color-level('red', 800);
  red-red-900: palette-color-level('red', 900);

  grey-grey-50: palette-color-level('grey', 50);
  grey-grey-100: palette-color-level('grey', 100);
  grey-grey-200: palette-color-level('grey', 200);
  grey-grey-300: palette-color-level('grey', 300);
  grey-grey-400: palette-color-level('grey', 400);
  grey-grey-500: palette-color-level('grey', 500);
  grey-grey-600: palette-color-level('grey', 600);
  grey-grey-700: palette-color-level('grey', 700);
  grey-grey-800: palette-color-level('grey', 800);
  grey-grey-900: palette-color-level('grey', 900);
}
</style>
