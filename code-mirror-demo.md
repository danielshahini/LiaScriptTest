# CodeMirror in LiaScript (Working Example)

```html
<div id="editor"></div>
<button id="runBtn">Run</button>
<pre id="output"></pre>

<!-- Load CodeMirror from CDN (pre-bundled, no import) -->
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/codemirror@5.65.16/lib/codemirror.css">
<script src="https://cdn.jsdelivr.net/npm/codemirror@5.65.16/lib/codemirror.js"></script>
<script src="https://cdn.jsdelivr.net/npm/codemirror@5.65.16/mode/javascript/javascript.js"></script>

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

<script>
  setTimeout(() => {
    // Initialize CodeMirror
    const editor = CodeMirror(document.getElementById("editor"), {
      value: 'console.log("Hello LiaScript + CodeMirror!");',
      mode: "javascript",
      lineNumbers: true
    });

    // Run button logic
    document.getElementById("runBtn").addEventListener("click", () => {
      const code = editor.getValue();
      try {
        const result = eval(code);
        document.getElementById("output").textContent =
          (result !== undefined ? result : "") + "\n(See console for logs)";
      } catch (err) {
        document.getElementById("output").textContent = "Error: " + err.message;
      }
    });
  }, 500); // Delay to ensure DOM is ready
</script>
