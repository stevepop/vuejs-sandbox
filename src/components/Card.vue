<!-- Card.vue -->
<template>
  <div class="card">
    <div class="card-body">
        <h5 class="card-title">
            <slot name="title"></slot>
        </h5>
        <p class="card-text">
            <slot name="body"></slot>
        </p>
    </div>
  </div>
</template>

<script>
export default {
    
}
</script>
