<template>
  <base-dialog v-if="isInputInvalid" title="Invalid Inputs!" @close="confirmErrorMsg">
    <template #default>
      <p>Unfortunately, at least one input is not valid!</p>
      <p>Please check all the inputs and make sure you've entred at least some non-space characters.</p>
    </template>
    <template #actions>
      <base-button @click="confirmErrorMsg">Okay</base-button>
    </template>
  </base-dialog>
  
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Title</label>
        <input type="text" name="title" id="tilte" ref="titleInput">
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" name="description" rows="3" ref="descInput"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input type="url" name="link" id="link" ref="linkInput">
      </div>
      <div>
        <base-button type="submit"> Add Resource </base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
import BaseButton from '../UI/BaseButton.vue';
export default {
  components: { BaseButton },
  data() {
    return {
      isInputInvalid: false
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDesc = this.$refs.descInput.value;
      const enteredLink = this.$refs.linkInput.value;

      if (enteredTitle.trim() === '' || enteredDesc.trim() === '' || enteredLink.trim() === '') {
        this.isInputInvalid = true;
        return;
      }
      this.addNewResource(enteredTitle, enteredDesc, enteredLink);
      // resetting form values
      this.$refs.titleInput.value = '';
      this.$refs.descInput.value = '';
      this.$refs.linkInput.value = '';
    },
    confirmErrorMsg() {
      this.isInputInvalid = false;
    }
  },
  inject: ['addNewResource']
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