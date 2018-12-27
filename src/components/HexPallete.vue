<template>
  <div class="container">
    <div class="pallete" v-for="(colourBand,index) in colourBands" v-bind:key="index" v-bind:style="{ backgroundColor: colourBand.colour }">
      <p>{{ colourBand.name }}</p>
      <p>{{ colourBand.colour }}</p>
      <p>{{ hexToRGBA( colourBand.colour, '1.0') }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HexPalette',
  data() {
    return {
      colourBands: [
        { name: 'Sephiroth', colour: '#23272a' },
        { name: 'Barrett Slate', colour: '#3f4354' },
        { name: 'Nocobo Dark', colour: '#34344a' },
        { name: 'Kuja Boy Blue', colour: '#7289da' },
        { name: 'Behemothurple', colour: '#636aa5' },
      ],
    };
  },
  methods: {
    hexToRGBA (hex, opacity) {
      return 'rgba(' + (hex = hex.replace('#', '')).match(new RegExp('(.{' + hex.length/3 + '})', 'g')).map(function (l) {
        return parseInt(hex.length % 2 ? l + l : l, 16)
      }).concat(opacity || 1).join(',') + ')';
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

$enable-rounded: true !default;

$border-radius: 0.25rem !default;
$border-width: 2px !default;

$pallete-padding-y:                   0.75rem !default;
$pallete-padding-x:                   1.25rem !default;
$pallete-margin-bottom:               1rem !default;
$pallete-border-radius:               $border-radius !default;
$pallete-border-width:                $border-width !default;

@mixin border-radius($radius: $border-radius) {
  @if $enable-rounded {
    border-radius: $radius;
  }
}

.pallete {
  position: relative;

  padding: $pallete-padding-y $pallete-padding-x;
  margin-bottom: $pallete-margin-bottom;

  border: $pallete-border-width solid rgba(0,0,0,.1);

  @include border-radius($pallete-border-radius);

  box-sizing: border-box;

  transition: all .12s ease-out;

  &:hover {
    cursor: pointer;
    box-shadow: 0 4px 14px 0 rgba(0,0,0,.4);
    top: -4px;
  }
}
</style>
