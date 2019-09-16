<template>
  <div class="column">
    <div class="card">
      <header class="card-header">
        <p class="card-header-title has-text-grey">
          {{ title }}
        </p>
        <div class="content has-text-centered">
          <b-icon
            size="is-large"
            type="is-primary"
          />
        </div>
      </header>
      <div class="card-content">
        <slot />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>
