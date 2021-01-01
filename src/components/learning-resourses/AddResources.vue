<template>
  <base-card>
    <form @submit.prevent="saveData">
      <div class="form-control">
        <lable for="title"> Title </lable>
        <input id="title" name="title" type="text" ref="titleInput" />
      </div>

      <div class="form-control">
        <lable for="desc"> Description </lable>
        <textarea id="desc" name="desc" rows="3" ref="descInput" ></textarea>
      </div>

      <div class="form-control">
        <lable for="link"> Link </lable>
        <input id="link" name="link" type="url" ref="linkInput" />
      </div>

      <div>
        <base-button type="submit"> Add Resourse </base-button>
      </div>
    </form>
  </base-card>

  <base-dialog v-if="inputIsInValid" title="Invalid Input" @close="closePopUp">
    <template #default>
      <p> At least one inpu value is invalid </p>
      <p> Please check all inputs and write at leasst some characters in each input  </p>
    </template>

    <template #actions>
      <base-button @click='closePopUp'> Okay </base-button>
    </template>
  </base-dialog>
</template>

<script>
import BaseButton from '../ui/BaseButton.vue';
export default {
  components: {
    BaseButton
  },
  inject: ['addResource'],
  data() {
    return {
      inputIsInValid: false,
    }
  },
  methods: {
    saveData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDesc = this.$refs.descInput.value;
      const enteredUrl = this.$refs.linkInput.value;

      if ( enteredTitle.trim() == "" || enteredDesc.trim() == "" || enteredUrl.trim() == "" ) {
        this.inputIsInValid = true;
        return;
      }

      this.addResource(enteredTitle, enteredDesc, enteredUrl)
    },
    closePopUp() {
      this.inputIsInValid = false;
    },
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