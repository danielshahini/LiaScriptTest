@CM._editor
<div id="cm-wrap-@0" style="border: 1px solid #ddd; padding: 8px; border-radius: 6px;">

  <div style="margin-bottom: 8px;">
    <button id="cm-run-@0">Run</button>
    <button id="cm-clear-@0" style="margin-left: 6px;">Clear output</button>
  </div>

  <!-- FLEX ROW -->
  <div style="display:flex; gap:12px; align-items:stretch; width:100%;">

    <!-- LEFT: Editor -->
    <div style="flex:1 1 0; min-width:0;">
      <div style="margin: 6px 0; font-weight: 600;">Code</div>
      <textarea id="cm-src-@0" style="width: 100%; min-height: 220px;">console.log("Hello from CodeMirror");</textarea>
    </div>

    <!-- RIGHT: Output -->
    <div style="flex:1 1 0; min-width:0;">
      <div style="margin: 6px 0; font-weight: 600;">Output</div>
      <pre id="cm-out-@0" style="white-space: pre-wrap; border: 1px solid #eee; padding: 8px; min-height: 220px; background: #fafafa; margin:0;"></pre>
    </div>

  </div>
</div>

<script>
(function () {
  var textarea = document.getElementById("cm-src-@0");
  var outEl = document.getElementById("cm-out-@0");
  var runBtn = document.getElementById("cm-run-@0");
  var clearBtn = document.getElementById("cm-clear-@0");
  if (!textarea || !outEl || !runBtn || !clearBtn) return;

  if (textarea.dataset.cmInitialized) return;
  textarea.dataset.cmInitialized = "1";

  var editor = CodeMirror.fromTextArea(textarea, {
    lineNumbers: true,
    mode: "javascript"
  });

  // Make sure CodeMirror doesn't force layout weirdness
  editor.setSize("100%", 220);

  function append(line) { outEl.textContent += line + "\n"; }

  clearBtn.addEventListener("click", function () { outEl.textContent = ""; });

  runBtn.addEventListener("click", function () {
    outEl.textContent = "";

    var originalLog = console.log;
    console.log = function () {
      var msg = Array.prototype.slice.call(arguments).map(String).join(" ");
      append(msg);
      originalLog.apply(console, arguments);
    };

    try {
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

# Tests

@CM
