<script>

export default {
  name: "HeaderSpaceInfo",
  data() {
    return {
      space: new Decimal(0),
      nerf: new Decimal(0),
    };
  },
  computed: {
    effectDisplay() {
      return `Space: ${format(this.space, 2)} | AM ^ (1/${format(this.nerf, 2, 3)})`;
    },
  },
  methods: {
    update() {
      this.nerf = player.antimatter.max(10).log10() ** (1/0.85) / player.antimatter.max(10).log10();
      this.space = Decimal.pow10(this.nerf).div(10);
    },
  },
};
</script>

<template>
  <div>
    <br>
    {{ effectDisplay }}
  </div>
</template>

<style scoped>

</style>