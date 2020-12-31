<template>
  <base-card>
    <form @submit.prevent="saveData">
      <div class="form-control">
        <lable for="title"> Title </lable>
        <input id="title" name="title" type="text" ref="titleInput" required/>
      </div>

      <div class="form-control">
        <lable for="desc"> Description </lable>
        <textarea id="desc" name="desc" rows="3" ref="descInput" required></textarea>
      </div>

      <div class="form-control">
        <lable for="link"> Link </lable>
        <input id="link" name="link" type="url" ref="linkInput" required/>
      </div>

      <div>
        <base-button type="submit"> Add Resourse </base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResource'],
  methods: {
    saveData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDesc = this.$refs.descInput.value;
      const enteredUrl = this.$refs.linkInput.value;

      this.addResource(enteredTitle, enteredDesc, enteredUrl)
    }
  },
}
</script>

<style scoped>
  label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
  }

  input,
  textarea {
    display: block;
    width: 100%;
    font: inherit;
    padding: 0.15rem;
    border: 1px solid #ccc;
  }

  input:focus,
  textarea:focus {
    outline: none;
    border-color: #3a0061;
    background-color: #f7ebff;
  }

  .form-control {
    margin: 1rem 0;
  }
</style>