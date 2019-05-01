<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <slot></slot>
    <input v-if="!this.editMode" type="button" @click="onEditClicked" value="Edit">
    <input v-if="this.editMode" type="button" @click="onOKClicked" value="OK">
    <input v-if="this.editMode" type="button" @click="onCancelClicked" value="Cancel">
  </div>
</template>

<script>
export default {
  props: {
    msg: String
  },
  name: "EditableForm",
  data: function() {
    return { editMode: false };
  },
  methods: {
    setEditMode: function(value) {
      if (value === this.editMode) return;
      this.editMode = value;
      this.$emit("editModeChanged");
    },
    onEditClicked: function() {
      this.setEditMode(true);
    },
    onOKClicked: function() {
      this.setEditMode(false);
    },
    onCancelClicked: function() {
      this.setEditMode(false);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
