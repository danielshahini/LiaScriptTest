<!--
author: Your Name
title: LiaScript + CodeMirror Demo
version: 1.0.0
language: en
-->

# LiaScript + CodeMirror Live Editor

This lesson shows how to integrate **CodeMirror 6** into LiaScript so learners can edit and run code interactively.

---

## Live JavaScript Editor

Below is a live CodeMirror editor.  
Type your code and click **Run** to see the output.

```html
<div id="editor"></div>
<button id="runBtn">Run</button>
<pre id="output"></pre>

<!-- Load CodeMirror 6 from CDN -->
<script type="module">
  import { EditorView, basicSetup } from "https://esm.sh/@codemirror/basic-setup";
  import { javascript } from "https://esm.sh/@codemirror/lang-javascript";

  // Initialize CodeMirror
  const startState = EditorView.state({
    doc: `console.log("Hello LiaScript + CodeMirror!");`,
    extensions: [basicSetup, javascript()]
  });

  const view = new EditorView({
    state: startState,
    parent: document.getElementById("editor")
  });

  // Run button logic
  document.getElementById("runBtn").addEventListener("click", () => {
    const code = view.state.doc.toString();
    try {
      const result = eval(code); // Run JS code
      document.getElementById("output").textContent =
        (result !== undefined ? result : "") + "\n(See console for logs)";
    } catch (err) {
      document.getElementById("output").textContent = "Error: " + err.message;
    }
  });
</script>

<style>
  #editor {
    border: 1px solid #ccc;
    font-size: 14px;
    height: 200px;
    margin-bottom: 10px;
  }
  #runBtn {
    padding: 5px 10px;
    margin-bottom: 10px;
  }
  #output {
    background: #f4f4f4;
    padding: 10px;
    border: 1px solid #ccc;
    min-height: 50px;
  }
</style>
