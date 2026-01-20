<!--
script: https://unpkg.com/@codemirror/basic-setup@latest/dist/index.global.js
script: https://unpkg.com/@codemirror/lang-javascript@latest/dist/index.global.js
link: https://codemirror.net/try/theme/one-dark.css

@codemirror(@0):
<div class="cm-wrapper" data-lang="@0"></div>
<script>
  const div = document.currentScript.previousElementSibling;
  const lang = div.dataset.lang;

  window.CodeMirrorSetup = window.CodeMirrorSetup || {};

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
</script>
-->

# 👋 CodeMirror Embedded in LiaScript

This is a live editor:

@codemirror(js)
