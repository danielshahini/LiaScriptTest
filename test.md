<!--
link: https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.16/codemirror.min.css
script: https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.16/codemirror.min.js
script: https://cdnjs.cloudflare.com/ajax/libs/codemirror/5.65.16/mode/javascript/javascript.min.js

@CM._editor
<textarea id="cm-@0" style="width: 100%; min-height: 160px;">console.log("Hello from CodeMirror");</textarea>
<script>
(function () {
  var el = document.getElementById("cm-@0");
  if (!el) return;

  // Prevent double-init if LiaScript re-renders
  if (el.dataset.cmInitialized) return;
  el.dataset.cmInitialized = "1";

  CodeMirror.fromTextArea(el, {
    lineNumbers: true,
    mode: "javascript"
  });
})();
</script>
@end

@CM: @CM._editor(@uid)
-->

# CodeMirror test

@CM
