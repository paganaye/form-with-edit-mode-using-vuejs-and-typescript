<template>
  <div class="editableTextbox">
    <label>{{ label }}</label>
    <input v-if="editMode" :value="this.value" @input="onInputChanged">
    <span v-else>{{this.value}}</span>
  </div>
</template>

<script>
export default {
  props: {
    label: String,
    value: String
  },
  name: "EditableTextbox",
  data: function() {
    return { editMode: false };
  },
  mounted: function() {
    const parentForm = this.findParentForm();
    if (parentForm) {
      this.editMode = parentForm.editMode;
      parentForm.$on(
        "editModeChanged",
        () => (this.editMode = parentForm.editMode)
      );
    }
  },
  methods: {
    findParentForm: function() {
      let parent = this.$parent;
      while (parent) {
        if (parent.editMode !== undefined) return parent;
        parent = parent.$parent;
      }
    },
    onInputChanged: function(e) {
      this.$emit("input", e.target.value);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.editableTextbox {
  margin: 1em;
}
label {
  margin-right: 0.5em;
}
</style>
