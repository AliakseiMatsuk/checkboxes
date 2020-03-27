<template lang="pug">
  #app
    .wrapper
      .container
        .row
          .col
            h2 Unhecked
          .col
            h2 Checked
        .row
          .col
            b-toggle(v-model="isChecked1", disabled, label="Disabled")
          .col
            b-toggle(v-model="isChecked2", disabled, label="Disabled")
        .row
          .col
            b-toggle(v-model="isChecked3", label="Enabled")
          .col
            b-toggle(v-model="isChecked4", label="Enabled")
</template>

<script>
import BToggle from "@/components/b-toggle.vue";

export default {
  name: "App",
  components: {
    BToggle
  },
  data() {
    return {
      isChecked1: false,
      isChecked2: true,
      isChecked3: false,
      isChecked4: true
    };
  }
};
</script>

<style lang="stylus">
@import 'assets/optimize'

.wrapper
  display flex
  justify-content center
  align-items center
  height 100vh

.container
  width 100%
  max-width 970px
  margin 0 auto
  padding 0 15px

.row
  display flex
  &:not(:last-child)
    margin-bottom 50px

.col
  flex-basis 50%
</style>
