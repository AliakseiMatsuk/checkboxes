<template lang="pug">
  .b-toggle
    label.b-toggle__wrapper(:class="{'_disabled' : disabled}")
      input.b-toggle__input(
      :checked="value",
      :disabled="disabled",
      type="checkbox",
      @change="$emit('input', $event.target.checked)")
      span.b-toggle__element
      span.b-toggle__label(v-if="label") {{ label }}
</template>

<script>
export default {
  name: "bToggle",
  props: {
    value: {
      type: Boolean,
      default: false
    },
    disabled: {
      type: Boolean,
      default: false
    },
    label: {
      type: String,
      default: ''
    }
  },
};
</script>

<style lang="stylus">
$primary = #6200EE
$dark = #000000
$lightest = #FFFFFF
$gray = #757575
$opacity = .26

ps()
  display block
  content ""
  position absolute

.b-toggle
  &__input
    width 0
    height 0
    opacity 0
    overflow hidden
    position absolute
    &:checked
      & + .b-toggle__element
        border-color transparent
        background-color $primary
        &:before
          background-color $primary
        &:after
          opacity 1
    &:hover,
    &:focus,
    &:active
      & + .b-toggle__element
        &:before
          opacity $opacity
    &:active
      & + .b-toggle__element
        &:before
          background-color $primary
    &[disabled]
      & + .b-toggle__element
        border-color rgba($dark, $opacity)
        &:before
          display none
      &:checked
        & + .b-toggle__element
          border-color transparent
          background-color rgba($dark, $opacity)
  &__element
    width 18px
    height 18px
    flex-shrink 0
    position relative
    border 2px solid $gray
    border-radius 2px
    background-color transparent
    will-change background-color, border-color
    transition background-color .3s ease-in-out, border-color .3s ease-in-out
    &:before
      ps()
      border-radius 50%
      opacity 0
      top -13px
      left -13px
      right -13px
      bottom -13px
      background-color $dark
      will-change opacity, background-color
      transition opacity .3s ease-in-out, background-color .3s ease-in-out
    &:after
      ps()
      top 3px
      left 1px
      margin auto 0
      width 12px
      height 6px
      border-left 2px solid $lightest
      border-bottom 2px solid $lightest
      opacity 0
      transform rotate(-55deg)
      transition opacity .3s ease-in-out
  &__wrapper
    display inline-flex
    align-items center
    &:not(._disabled)
      cursor pointer
  &__label
    color $dark
    font-size 16px
    margin-left 20px
</style>
