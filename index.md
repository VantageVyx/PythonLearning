# Python Stufff
<script src="https://cdn.jsdelivr.net/pyodide/v0.27.0/full/pyodide.js"></script>

<textarea id="code" rows="10" style="width:100%; font-family:monospace;">
print("Hello, World!")
</textarea>

<br>
<button onclick="runCode()">Run</button>

<pre id="output" style="background:#1e1e1e; color:#00ff00; padding:10px;"></pre>

<script>
  let pyodide;
  async function loadPy() {
    pyodide = await loadPyodide();
  }
  loadPy();

  async function runCode() {
    let code = document.getElementById("code").value;
    try {
      let result = await pyodide.runPythonAsync(code);
      document.getElementById("output").innerText = result ?? "";
    } catch (err) {
      document.getElementById("output").innerText = err;
    }
  }
</script>
