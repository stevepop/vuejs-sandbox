<template>
    <div class="field">
        <label for="name" class="label">{{ name }}</label>
        <input type="text" name="name" :placeholder="holderText">
    </div>
</template>

<script>
export default {
    props: ['name', 'placeholder'],

    computed: {
        holderText() {
            return this.placeholder
        }
    }
}
</script>

<style>
  .field {
      margin-bottom: 10px;
  }
  .label {
      min-width: 100px;
  }
</style>


