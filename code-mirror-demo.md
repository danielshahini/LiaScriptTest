# CodeMirror Macro Definition
<!--
author: You

script: https://unpkg.com/@codemirror/basic-setup@latest/dist/index.global.js
script: https://unpkg.com/@codemirror/lang-javascript@latest/dist/index.global.js
link: https://codemirror.net/try/theme/one-dark.css

@codemirror(@0):
<script run-once modify="false">
  const id = "cm-" + Math.random().toString(36).substring(2);
  const doc = "console.log('Hello from CodeMirror!');";

  send.lia(`HTML: <div id="${id}" class="cm-wrapper" style="border: 1px solid #aaa; margin: 1em 0;"></div>`);

  setTimeout(() => {
    const parent = document.getElementById(id);
    if (!parent) return;

    new window.cm.EditorView({
      doc,
      extensions: [
        window.cm.basicSetup,
        window.cm.javascript.javascript()
      ],
      parent
    });
  }, 100);
</script>
-->

# CodeMirror in LiaScript

Below is a working CodeMirror editor injected via a LiaScript macro:

@codemirror(js)
