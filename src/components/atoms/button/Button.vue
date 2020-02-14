<template>
  <button
    class="mid-button"
    @click="handleClick"
    :disabled="disabled || loading"
    :class="[
      type ? 'mid-button--' + type : '',
      size ? 'mid-button--' + size : '',
      {
        'is-disabled': disabled,
        'is-loading': loading,
      },
    ]"
  >
    <span v-if="$slots.default"><slot></slot></span>
  </button>
</template>

<script>
/**
 * Buttons are generally used for interface actions. Suitable for all-purpose use.
 * Defaults to appearance that has white background with grey border.
 * Primary style should be used only once per view for main call-to-action.
 */
export default {
  name: "MidButton",
  status: "prototype",
  release: "3.5.0",
  props: {
    /**
     * Type of the button
     * `primary, success, warning, danger, info, default`
     */
    type: {
      type: String,
      default: "default",
      validator: value => {
        return value.match(/(primary|success|warning|danger|info|default)/)
      },
    },
    /**
     * Size of the button
     * `small, medium`
     */
    size: {
      type: String,
      default: "medium",
      validator: value => {
        return value.match(/(mini|small|medium)/)
      },
    },
    /**
     * Whether the button is disabled or not.
     * `true, false`
     */
    disabled: {
      type: Boolean,
      default: false,
    },

    /**
     * Whether the button is loading or not.
     * `true, false`
     */
    loading: {
      type: Boolean,
      default: false,
    },
  },
}
</script>

<style lang="scss" scoped>
@import "button.scss";
</style>

<docs>
  ```jsx
  <div>
    <MidButton type="primary">Primary</MidButton>
    <MidButton type="success">Success</MidButton>
    <MidButton type="warning">Warning</MidButton>
    <MidButton type="danger">Danger</MidButton>
    <MidButton type="info">Info</MidButton>
    <MidButton>Default</MidButton>
    <pre />
    <MidButton type="primary" disabled>Primary</MidButton>
    <MidButton type="success" disabled>Success</MidButton>
    <MidButton type="warning" disabled>Warning</MidButton>
    <MidButton type="danger" disabled>Danger</MidButton>
    <MidButton type="info" disabled>Info</MidButton>
    <MidButton disabled>Default</MidButton>
    <pre />
    <MidButton type="primary" size="mini">Mini</MidButton>
    <MidButton type="primary" size="small">Small</MidButton>
    <MidButton type="primary">Normal</MidButton>
  </div>
  ```
</docs>
