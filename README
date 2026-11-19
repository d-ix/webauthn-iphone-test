
<!DOCTYPE html>
<html lang="ru">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>WebAuthn iPhone Test</title>
<style>
body {
  font-family: system-ui;
  background: #111;
  color: #eee;
  padding: 25px;
}
.card {
  max-width: 500px;
  margin: 30px auto;
  padding: 25px;
  background: #222;
  border-radius: 14px;
}
button {
  padding: 12px 20px;
  border: 0;
  border-radius: 8px;
  cursor: pointer;
}
pre {
  white-space: pre-wrap;
  overflow-wrap: anywhere;
}
</style>
</head>
<body>
<div class="card">
<h2>WebAuthn Device Check</h2>
<p>Проверка поддержки Passkeys и WebAuthn.</p>
<button onclick="runTest()">Запустить проверку</button>
<pre id="result">Ожидание...</pre>
</div>

<script>
async function runTest() {
  const output = document.getElementById("result");
  const lines = [];

  lines.push("Browser: " + navigator.userAgent);
  lines.push("Secure context: " + window.isSecureContext);
  lines.push("WebAuthn: " +
    ("credentials" in navigator));
  lines.push("PublicKeyCredential: " +
    ("PublicKeyCredential" in window));

  if (window.PublicKeyCredential) {
    try {
      const available =
        await PublicKeyCredential
          .isUserVerifyingPlatformAuthenticatorAvailable();

      lines.push("Platform authenticator: " + available);
    } catch (error) {
      lines.push("Authenticator error: " + error.message);
    }
  }

  output.textContent = lines.join("\n");
}
</script>
</body>
</html>
