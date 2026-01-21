<!--
link: https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.16/codemirror.min.css
script: https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.16/codemirror.min.js
script: https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.16/mode/javascript/javascript.min.js

@CM._editor
<div id="cm-wrap-@0" style="border: 1px solid #ddd; padding: 8px; border-radius: 6px;">
  <div style="margin-bottom: 8px;">
    <button id="cm-run-@0">Run</button>
    <button id="cm-clear-@0" style="margin-left: 6px;">Clear output</button>
  </div>

  <textarea id="cm-src-@0" style="width: 100%; min-height: 160px;">console.log("Hello from CodeMirror");</textarea>

  <div style="margin-top: 10px; font-weight: 600;">Output</div>
  <pre id="cm-out-@0" style="white-space: pre-wrap; border: 1px solid #eee; padding: 8px; min-height: 80px; background: #fafafa;"></pre>
</div>

<script>
(function () {
  var textarea = document.getElementById("cm-src-@0");
  var outEl = document.getElementById("cm-out-@0");
  var runBtn = document.getElementById("cm-run-@0");
  var clearBtn = document.getElementById("cm-clear-@0");
  if (!textarea || !outEl || !runBtn || !clearBtn) return;

  // Avoid double-init on re-render
  if (textarea.dataset.cmInitialized) return;
  textarea.dataset.cmInitialized = "1";

  var editor = CodeMirror.fromTextArea(textarea, {
    lineNumbers: true,
    mode: "javascript"
  });

  function append(line) {
    outEl.textContent += line + "\n";
  }

  clearBtn.addEventListener("click", function () {
    outEl.textContent = "";
  });

  runBtn.addEventListener("click", function () {
    outEl.textContent = "";

    // Capture console.log during run
    var originalLog = console.log;
    console.log = function () {
      var msg = Array.prototype.slice.call(arguments).map(String).join(" ");
      append(msg);
      originalLog.apply(console, arguments);
    };

    try {
      // Execute user code
      var code = editor.getValue();
      (new Function(code))();
    } catch (e) {
      append("Error: " + (e && e.message ? e.message : String(e)));
    } finally {
      console.log = originalLog;
    }
  });
})();
</script>
@end

@CM: @CM._editor(@uid)
-->


# CodeMirror test

@CM


