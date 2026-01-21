<!--
author: You

script: https://unpkg.com/@codemirror/basic-setup@latest/dist/index.global.js
script: https://unpkg.com/@codemirror/lang-javascript@latest/dist/index.global.js
link: https://codemirror.net/try/theme/one-dark.css

@codemirror(@0):
<script run-once modify="false">
const id = "cm-" + Math.random().toString(36).substring(2);
const doc = `console.log("Hello from CodeMirror!");`;

send.lia(`HTML: <div id="${id}" class="cm-wrapper" style="border: 1px solid #aaa; margin: 1em 0;"></div>`);

function mountCM(retries = 10) {
  const parent = document.getElementById(id);
  if (!parent) {
    if (retries > 0) {
      setTimeout(() => mountCM(retries - 1), 200);
    } else {
      send.lia("LIA: stop");
    }
    return;
  }

  new window.cm.EditorView({
    doc,
    extensions: [
      window.cm.basicSetup,
      window.cm.javascript.javascript()
    ],
    parent
  });
}

setTimeout(() => mountCM(), 300);
</script>
-->

# CodeMirror Editor (Working Version)

@codemirror(js)
