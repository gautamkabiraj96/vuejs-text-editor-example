<template>
  <div id="app">
    <div class="np-credits">www.nightprogrammer.com</div>
    <div @click="saveData()" v-if="editorData" class="np-save-btn">Save</div>
    <div @click="clearData()" v-if="editorData" class="np-save-btn">Clear</div>

    <div style="height: auto">
      <ckeditor
        :editor="editor"
        v-model="editorData"
        :config="editorConfig"
      ></ckeditor>
    </div>
    <div v-if="dataToSave">
      <h4>Parsed data:</h4>
      {{ dataToSave }}
    </div>
  </div>
</template>

<script>
import ClassicEditor from "@ckeditor/ckeditor5-build-classic";

export default {
  name: "App",
  data() {
    return {
      editor: ClassicEditor,
      editorData: "",
      editorConfig: {
        // todo confg
      },
      dataToSave: "",
    };
  },
  methods: {
    saveData() {
      this.dataToSave = this.editorData;
    },
    clearData() {
      this.dataToSave = this.editorData = "";
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.np-credits {
  font-size: 12px;
  margin-bottom: 12px;
}
.np-save-btn {
  background: #eee;
  border-radius: 4px;
  padding: 2px;
  width: 100px;
  text-align: center;
  margin-bottom: 10px;
  cursor: pointer;
}
</style>
