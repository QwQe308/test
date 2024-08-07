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
      return `Space: ${format(this.space, 2, 3)} | AM ^ (1/${format(this.nerf, 2, 3)})`;
    },
  },
  methods: {
    update() {
      this.space = Decimal.pow10(player.antimatter.add(10).log10() ** (1/0.9) / player.antimatter.add(10).log10()).sub(10).div(10);
      this.nerf = this.space.add(1).mul(10).log10();
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