<!--
author: Your Name
title: LiaScript + CodeMirror Demo
version: 1.0.0
language: en

@CodeMirrorJS
<div id="editor-@0"></div>
<button id="runBtn-@0">Run</button>
<pre id="output-@0"></pre>

<script type="module">
  import { EditorView, basicSetup } from "https://esm.sh/@codemirror/basic-setup";
  import { EditorState } from "https://esm.sh/@codemirror/state";
  import { javascript } from "https://esm.sh/@codemirror/lang-javascript";

  const parent = document.getElementById("editor-@0");
  const runBtn = document.getElementById("runBtn-@0");
  const output = document.getElementById("output-@0");

  const startState = EditorState.create({
    doc: `console.log("Hello LiaScript + CodeMirror!");`,
    extensions: [basicSetup, javascript()]
  });

  const view = new EditorView({
    state: startState,
    parent
  });

  runBtn.addEventListener("click", () => {
    const code = view.state.doc.toString();

    const logs = [];
    const origLog = console.log;
    console.log = (...args) => logs.push(args.join(" "));

    try {
      const result = (0, eval)(code);
      const resultText = result !== undefined ? String(result) + "\n" : "";
      output.textContent =
        resultText + (logs.length ? logs.join("\n") + "\n" : "");
    } catch (err) {
      output.textContent = "Error: " + err.message;
    } finally {
      console.log = origLog;
    }
  });
</script>

<style>
  #editor-@0 {
    border: 1px solid #ccc;
    font-size: 14px;
    height: 200px;
    margin-bottom: 10px;
  }
  #runBtn-@0 {
    padding: 5px 10px;
    margin-bottom: 10px;
  }
  #output-@0 {
    background: #f4f4f4;
    padding: 10px;
    border: 1px solid #ccc;
    min-height: 50px;
    white-space: pre-wrap;
  }
</style>
@end
-->

# LiaScript + CodeMirror Live Editor

Below is a live CodeMirror editor. Type code and click Run.

@CodeMirrorJS(@uid)
