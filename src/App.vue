<template>
  <div id="app">
    <EditableForm msg="Editable form">
      <EditableTextbox label="textbox1" v-model="textbox1"/>
      <EditableTextbox label="textbox2" v-model="textbox2"/>
      <pre>{{textbox1 + " " + textbox2 }}</pre>
    </EditableForm>
  </div>
</template>

<script>
import EditableForm from "./components/EditableForm";
import EditableTextbox from "./components/EditableTextbox";

export default {
  name: "App",
  data: function() {
    return { textbox1: "Hello", textbox2: "World" };
  },
  computed: {},
  components: {
    EditableForm,
    EditableTextbox
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
