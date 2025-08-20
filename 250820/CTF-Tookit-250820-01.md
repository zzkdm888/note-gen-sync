![image.png](https://cdn.jsdelivr.net/gh/zzkdm888/note-gen-image-sync@main/2025-08/957a1f23-531d-4abe-9a49-c3b816172635.png)

<br>

---

<br>


[执行中...]

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>终极CTF工具集</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js"></script>
    <style>
        :root {
            --background-color: #0d0208;
            --text-color: #00ff41;
            --container-bg: #1a1a1a;
            --border-color: #00ff41;
            --input-bg: #101010;
            --button-bg: #00ff41;
            --button-text: #000000;
            --button-hover-bg: #ffffff;
            --button-hover-text: #000000;
        }

        body {
            background-color: var(--background-color);
            color: var(--text-color);
            font-family: 'Courier New', Courier, monospace;
            display: flex;
            justify-content: center;
            align-items: flex-start;
            min-height: 100vh;
            margin: 0;
            padding: 20px;
            overflow-x: hidden;
        }

        .container {
            width: 100%;
            max-width: 1200px;
            background-color: var(--container-bg);
            border: 1px solid var(--border-color);
            box-shadow: 0 0 15px var(--border-color);
            padding: 20px;
            animation: fadeIn 1s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: scale(0.95); }
            to { opacity: 1; transform: scale(1); }
        }

        h1 {
            text-align: center;
            text-shadow: 0 0 5px var(--text-color);
            margin-bottom: 30px;
            letter-spacing: 3px;
        }

        .tool-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .tool {
            background-color: var(--input-bg);
            border: 1px solid var(--border-color);
            padding: 15px;
            display: flex;
            flex-direction: column;
            transition: box-shadow 0.3s;
        }

        .tool:hover {
            box-shadow: 0 0 10px var(--border-color);
        }

        .tool h2 {
            margin-top: 0;
            margin-bottom: 10px;
            font-size: 1.2em;
            border-bottom: 1px solid var(--border-color);
            padding-bottom: 5px;
        }

        .tool-controls {
            display: flex;
            gap: 10px;
            margin-bottom: 10px;
            align-items: center;
        }

        .tool-controls label {
            white-space: nowrap;
        }

        .tool-controls input[type="number"],
        .tool-controls select {
            background-color: #333;
            color: var(--text-color);
            border: 1px solid var(--border-color);
            padding: 5px;
            width: 60px;
        }
      
        .io-container {
            display: flex;
            flex-direction: column;
            gap: 10px;
            height: 100%;
        }

        textarea {
            width: 100%;
            height: 150px;
            background-color: var(--input-bg);
            color: var(--text-color);
            border: 1px dashed var(--border-color);
            padding: 10px;
            font-family: inherit;
            resize: vertical;
            box-sizing: border-box;
            transition: all 0.3s;
        }

        textarea:focus {
            outline: none;
            border-style: solid;
            box-shadow: 0 0 8px var(--border-color);
        }

        .output-container {
            position: relative;
            flex-grow: 1;
        }

        .copy-btn {
            position: absolute;
            top: 5px;
            right: 5px;
            background-color: var(--button-bg);
            color: var(--button-text);
            border: none;
            padding: 5px 8px;
            cursor: pointer;
            font-family: inherit;
            font-weight: bold;
            opacity: 0.7;
            transition: opacity 0.3s, background-color 0.3s;
        }

        .copy-btn:hover {
            opacity: 1;
            background-color: var(--button-hover-bg);
            color: var(--button-hover-text);
        }
      
        .copy-btn.copied {
            background-color: #008000;
            color: white;
        }

    </style>
</head>
<body>

    <div class="container">
        <h1>[ CTF TOOLKIT ]</h1>
        <div class="tool-grid">
            <!-- Base64 Encoder/Decoder -->
            <div class="tool">
                <h2>Base64 Encode/Decode</h2>
                <div class="io-container">
                    <textarea id="base64-input" placeholder="Input..."></textarea>
                    <div class="output-container">
                        <textarea id="base64-output" readonly placeholder="Output..."></textarea>
                        <button class="copy-btn" onclick="copyToClipboard('base64-output')">Copy</button>
                    </div>
                </div>
            </div>

            <!-- URL Encoder/Decoder -->
            <div class="tool">
                <h2>URL Encode/Decode</h2>
                <div class="io-container">
                    <textarea id="url-input" placeholder="Input..."></textarea>
                    <div class="output-container">
                        <textarea id="url-output" readonly placeholder="Output..."></textarea>
                        <button class="copy-btn" onclick="copyToClipboard('url-output')">Copy</button>
                    </div>
                </div>
            </div>

            <!-- Hash Generator -->
            <div class="tool">
                <h2>Hash Generator</h2>
                <div class="tool-controls">
                     <select id="hash-type">
                        <option value="md5">MD5</option>
                        <option value="sha1">SHA1</option>
                        <option value="sha256">SHA256</option>
                        <option value="sha512">SHA512</option>
                    </select>
                </div>
                <div class="io-container">
                    <textarea id="hash-input" placeholder="Input..."></textarea>
                    <div class="output-container">
                        <textarea id="hash-output" readonly placeholder="Output..."></textarea>
                        <button class="copy-btn" onclick="copyToClipboard('hash-output')">Copy</button>
                    </div>
                </div>
            </div>

            <!-- Caesar Cipher -->
            <div class="tool">
                <h2>Caesar Cipher</h2>
                 <div class="tool-controls">
                    <label for="caesar-shift">Shift:</label>
                    <input type="number" id="caesar-shift" value="3" min="1" max="25">
                </div>
                <div class="io-container">
                    <textarea id="caesar-input" placeholder="Input..."></textarea>
                    <div class="output-container">
                        <textarea id="caesar-output" readonly placeholder="Output..."></textarea>
                        <button class="copy-btn" onclick="copyToClipboard('caesar-output')">Copy</button>
                    </div>
                </div>
            </div>
             <!-- Morse Code -->
            <div class="tool">
                <h2>Morse Code</h2>
                <div class="io-container">
                    <textarea id="morse-input" placeholder="Input... (e.g., HELLO or .... . .-.. .-.. ---)"></textarea>
                    <div class="output-container">
                        <textarea id="morse-output" readonly placeholder="Output..."></textarea>
                        <button class="copy-btn" onclick="copyToClipboard('morse-output')">Copy</button>
                    </div>
                </div>
            </div>
             <!-- Unicode Converter -->
            <div class="tool">
                <h2>Unicode Converter</h2>
                 <div class="tool-controls">
                    <select id="unicode-format">
                        <option value="hex">Hex (\uXXXX)</option>
                        <option value="dec">Decimal (&#XXXX;)</option>
                    </select>
                </div>
                <div class="io-container">
                    <textarea id="unicode-input" placeholder="Input..."></textarea>
                    <div class="output-container">
                        <textarea id="unicode-output" readonly placeholder="Output..."></textarea>
                        <button class="copy-btn" onclick="copyToClipboard('unicode-output')">Copy</button>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        function copyToClipboard(elementId) {
            const textarea = document.getElementById(elementId);
            textarea.select();
            document.execCommand('copy');
          
            const btn = textarea.nextElementSibling;
            const originalText = btn.textContent;
            btn.textContent = 'Copied!';
            btn.classList.add('copied');
            setTimeout(() => {
                btn.textContent = originalText;
                btn.classList.remove('copied');
            }, 1500);
        }

        // --- Tool Logic ---

        // Base64
        const base64Input = document.getElementById('base64-input');
        const base64Output = document.getElementById('base64-output');
        base64Input.addEventListener('input', () => {
            const input = base64Input.value;
            try {
                // Try decoding first
                const decoded = atob(input);
                // Check if decoded string is valid text
                if (/^[\x00-\x7F]*$/.test(decoded)) {
                     base64Output.value = `DECODED:\n${decoded}`;
                } else {
                     throw new Error("Invalid ASCII");
                }
            } catch (e) {
                // If decoding fails, encode
                base64Output.value = `ENCODED:\n${btoa(input)}`;
            }
             if (input === "") {
                base64Output.value = "";
            }
        });

        // URL
        const urlInput = document.getElementById('url-input');
        const urlOutput = document.getElementById('url-output');
        urlInput.addEventListener('input', () => {
            const input = urlInput.value;
            try {
                const decoded = decodeURIComponent(input);
                if (decoded !== input) {
                    urlOutput.value = `DECODED:\n${decoded}`;
                } else {
                    urlOutput.value = `ENCODED:\n${encodeURIComponent(input)}`;
                }
            } catch (e) {
                 urlOutput.value = `ENCODED:\n${encodeURIComponent(input)}`;
            }
             if (input === "") {
                urlOutput.value = "";
            }
        });

        // Hash
        const hashInput = document.getElementById('hash-input');
        const hashOutput = document.getElementById('hash-output');
        const hashType = document.getElementById('hash-type');
        const hashHandler = () => {
            const input = hashInput.value;
            const type = hashType.value;
            if (input) {
                let hash;
                if (type === 'md5') hash = CryptoJS.MD5(input);
                if (type === 'sha1') hash = CryptoJS.SHA1(input);
                if (type === 'sha256') hash = CryptoJS.SHA256(input);
                if (type === 'sha512') hash = CryptoJS.SHA512(input);
                hashOutput.value = hash.toString(CryptoJS.enc.Hex);
            } else {
                hashOutput.value = '';
            }
        };
        hashInput.addEventListener('input', hashHandler);
        hashType.addEventListener('change', hashHandler);

        // Caesar Cipher
        const caesarInput = document.getElementById('caesar-input');
        const caesarOutput = document.getElementById('caesar-output');
        const caesarShift = document.getElementById('caesar-shift');
        const caesarHandler = () => {
            const input = caesarInput.value;
            const shift = parseInt(caesarShift.value, 10);
            if (isNaN(shift)) return;

            let result = '';
            for (let i = 0; i < input.length; i++) {
                let char = input[i];
                if (char.match(/[a-z]/i)) {
                    const code = input.charCodeAt(i);
                    if (code >= 65 && code <= 90) { // Uppercase
                        char = String.fromCharCode(((code - 65 + shift) % 26) + 65);
                    } else if (code >= 97 && code <= 122) { // Lowercase
                        char = String.fromCharCode(((code - 97 + shift) % 26) + 97);
                    }
                }
                result += char;
            }
            caesarOutput.value = result;
        };
        caesarInput.addEventListener('input', caesarHandler);
        caesarShift.addEventListener('input', caesarHandler);
      
        // Morse Code
        const morseInput = document.getElementById('morse-input');
        const morseOutput = document.getElementById('morse-output');
        const morseMap = {
            'A': '.-', 'B': '-...', 'C': '-.-.', 'D': '-..', 'E': '.', 'F': '..-.', 'G': '--.', 'H': '....',
            'I': '..', 'J': '.---', 'K': '-.-', 'L': '.-..', 'M': '--', 'N': '-.', 'O': '---', 'P': '.--.',
            'Q': '--.-', 'R': '.-.', 'S': '...', 'T': '-', 'U': '..-', 'V': '...-', 'W': '.--', 'X': '-..-',
            'Y': '-.--', 'Z': '--..', '1': '.----', '2': '..---', '3': '...--', '4': '....-', '5': '.....',
            '6': '-....', '7': '--...', '8': '---..', '9': '----.', '0': '-----', ' ': '/'
        };
        const revMorseMap = Object.fromEntries(Object.entries(morseMap).map(a => a.reverse()));
        morseInput.addEventListener('input', () => {
            const input = morseInput.value.trim();
            if (input === "") {
                morseOutput.value = "";
                return;
            }
            if (input.match(/^[.\-/\s]+$/)) { // Decode
                morseOutput.value = `DECODED:\n${input.split(' ').map(c => revMorseMap[c] || '').join('')}`;
            } else { // Encode
                morseOutput.value = `ENCODED:\n${input.toUpperCase().split('').map(c => morseMap[c] || '').join(' ')}`;
            }
        });
      
         // Unicode
        const unicodeInput = document.getElementById('unicode-input');
        const unicodeOutput = document.getElementById('unicode-output');
        const unicodeFormat = document.getElementById('unicode-format');

        const unicodeHandler = () => {
            const input = unicodeInput.value;
            const format = unicodeFormat.value;

            try { // Attempt to decode
                let decoded = input;
                if (input.includes('\\u')) {
                    decoded = input.replace(/\\u[\dA-F]{4}/gi, match => String.fromCharCode(parseInt(match.replace(/\\u/g, ''), 16)));
                } else if (input.includes('&#')) {
                    decoded = input.replace(/&#(\d+);/g, (match, dec) => String.fromCharCode(dec));
                }

                if (decoded !== input) {
                    unicodeOutput.value = `DECODED:\n${decoded}`;
                } else { // Encode
                    let result = '';
                    for (let i = 0; i < input.length; i++) {
                        if (format === 'hex') {
                            result += '\\u' + input.charCodeAt(i).toString(16).padStart(4, '0');
                        } else {
                            result += '&#' + input.charCodeAt(i) + ';';
                        }
                    }
                    unicodeOutput.value = `ENCODED:\n${result}`;
                }
            } catch (e) {
                 unicodeOutput.value = 'Invalid input for decoding.';
            }
            if (input === "") {
                unicodeOutput.value = "";
            }
        };

        unicodeInput.addEventListener('input', unicodeHandler);
        unicodeFormat.addEventListener('change', unicodeHandler);


    </script>
</body>
</html>
```

[执行完毕。]
