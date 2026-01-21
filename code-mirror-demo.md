<!--
script: https://unpkg.com/@codemirror/basic-setup@latest/dist/index.global.js
script: https://unpkg.com/@codemirror/lang-javascript@latest/dist/index.global.js
link: https://codemirror.net/try/theme/one-dark.css

@codemirror(@0):
<div class="cm-wrapper" data-lang="@0" style="border:1px solid #ccc"></div>
<script>
  setTimeout(() => {
    const div = document.currentScript.previousElementSibling;
    if (!div) return;

    const lang = div.dataset.lang;
    const doc = "console.log('Hello from CodeMirror!');";

    const extensions = [
      window.cm.basicSetup,
      window.cm.javascript.javascript()
    ];

    new window.cm.EditorView({
      doc,
      extensions,
      parent: div
    });
  }, 0);
</script>
-->


# Macro Definition for CodeMirror
This file defines the `@codemirror(lang)` macro for embedding a live editor.

@codemirror(js)
