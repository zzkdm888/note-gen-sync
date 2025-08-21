![image.png](https://cdn.jsdelivr.net/gh/zzkdm888/note-gen-image-sync@main/2025-08/14c73c45-f51d-40c8-b6b7-69f0612002c1.png)

<br>

---

<br>

[执行中...]

**核心分析与升级**

用户反馈工具集覆盖面不足。v2.0版本已具备了基础的编码和密码学工具，但距离一个“全面”的工具集尚有差距。CTF竞赛场景复杂多变，需要更专业、更深入的工具。

**v3.0 升级策略：**

1. **深化密码学 (Crypto):**

   * **维吉尼亚密码 (Vigenère Cipher):** 作为凯撒密码的升级版，是多表替换密码的经典代表，常见于中等难度的密码学题目。
   * **频率分析 (Frequency Analysis):** 任何古典密码破解的基础。通过统计密文中各字符出现的频率，可以为破解单表替换密码（甚至更复杂的密码）提供决定性线索。可视化图表能让频率分布一目了然。
2. **增强Web安全 (Web):**

   * **Cookie编辑器/解析器 (Cookie Editor):** 方便地解析、修改和重新编码Cookie字符串，常用于测试权限绕过、身份伪造等Web漏洞。
3. **覆盖逆向/杂项 (Reverse/Misc):**

   * **数字进制转换 (Number Base Converter):** 在处理底层数据、内存地址、文件格式时，二进制、八进制、十进制、十六进制之间的快速转换是必备技能。
   * **字符串转义/反转义 (String Escape/Unescape):** 在处理shellcode、网络负载、代码注入时，经常需要将特殊字符转换为其转义序列（如 `\x41`, `%41`）或反向操作。
   * **Brainfuck解释器 (Brainfuck Interpreter):** Brainfuck作为一种极简的深奥编程语言，是CTF杂项(Misc)类别中的常客。内置一个解释器可以快速运行和调试相关代码。

基于以上策略，对工具集进行大幅度功能扩展。以下是升级后的 `v3.0` 版本完整代码。

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>终极CTF工具集 v3.0</title>
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
        body { background-color: var(--background-color); color: var(--text-color); font-family: 'Courier New', Courier, monospace; display: flex; justify-content: center; align-items: flex-start; min-height: 100vh; margin: 0; padding: 20px; box-sizing: border-box; }
        .container { width: 100%; max-width: 1800px; background-color: var(--container-bg); border: 1px solid var(--border-color); box-shadow: 0 0 15px var(--border-color); padding: 20px; animation: fadeIn 1s ease-in-out; }
        @keyframes fadeIn { from { opacity: 0; transform: scale(0.95); } to { opacity: 1; transform: scale(1); } }
        h1 { text-align: center; text-shadow: 0 0 5px var(--text-color); margin-bottom: 30px; letter-spacing: 3px; }
        .tool-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(350px, 1fr)); gap: 20px; }
        .tool { background-color: var(--input-bg); border: 1px solid var(--border-color); padding: 15px; display: flex; flex-direction: column; transition: box-shadow 0.3s; }
        .tool:hover { box-shadow: 0 0 10px var(--border-color); }
        .tool h2 { margin-top: 0; margin-bottom: 10px; font-size: 1.2em; border-bottom: 1px solid var(--border-color); padding-bottom: 5px; }
        .tool-controls { display: flex; gap: 10px; margin-bottom: 10px; align-items: center; flex-wrap: wrap; }
        .tool-controls label { white-space: nowrap; }
        .tool-controls input, .tool-controls select, .tool-controls button { background-color: #333; color: var(--text-color); border: 1px solid var(--border-color); padding: 5px; font-family: inherit; }
        .tool-controls input[type="text"], .tool-controls input[type="number"] { width: 100px; }
        .tool-controls button { cursor: pointer; background-color: var(--border-color); color: var(--button-text); }
        .tool-controls button:hover { background-color: var(--button-hover-bg); color: var(--button-hover-text); }
        .io-container { display: flex; flex-direction: column; gap: 10px; height: 100%; flex-grow: 1; }
        textarea, .base-input { width: 100%; background-color: var(--input-bg); color: var(--text-color); border: 1px dashed var(--border-color); padding: 10px; font-family: inherit; resize: vertical; box-sizing: border-box; transition: all 0.3s; }
        textarea { height: 150px; }
        textarea:focus, .base-input:focus { outline: none; border-style: solid; box-shadow: 0 0 8px var(--border-color); }
        .output-container { position: relative; flex-grow: 1; display: flex; }
        .output-container textarea { flex-grow: 1; }
        .copy-btn { position: absolute; top: 5px; right: 5px; background-color: var(--button-bg); color: var(--button-text); border: none; padding: 5px 8px; cursor: pointer; font-family: inherit; font-weight: bold; opacity: 0.7; transition: opacity 0.3s, background-color 0.3s; z-index: 10;}
        .copy-btn:hover { opacity: 1; background-color: var(--button-hover-bg); color: var(--button-hover-text); }
        .copy-btn.copied { background-color: #008000; color: white; }
        #freq-output { font-family: monospace; white-space: pre; background-color: var(--input-bg); border: 1px solid var(--border-color); padding: 10px; overflow: auto; flex-grow: 1; }
        .freq-bar { height: 1em; background-color: var(--text-color); display: inline-block; vertical-align: middle; margin-left: 10px; box-shadow: 0 0 3px var(--text-color); }
        .base-converter .tool-controls { flex-direction: column; align-items: stretch; }
        .base-converter .base-row { display: flex; align-items: center; gap: 10px; }
        .base-converter label { flex-basis: 60px; text-align: right; }
        .base-converter input { flex-grow: 1; }
    </style>
</head>
<body>
<div class="container">
    <h1>[ CTF TOOLKIT v3.0 ]</h1>
    <div class="tool-grid">
        <!-- Base64 -->
        <div class="tool"><h2>Base64 Encode/Decode</h2><div class="io-container"><textarea id="base64-input" placeholder="Input..."></textarea><div class="output-container"><textarea id="base64-output" readonly placeholder="Output..."></textarea><button class="copy-btn" onclick="copyToClipboard('base64-output')">Copy</button></div></div></div>
        <!-- URL Encode/Decode -->
        <div class="tool"><h2>URL Encode/Decode</h2><div class="io-container"><textarea id="url-input" placeholder="Input..."></textarea><div class="output-container"><textarea id="url-output" readonly placeholder="Output..."></textarea><button class="copy-btn" onclick="copyToClipboard('url-output')">Copy</button></div></div></div>
        <!-- Hash Generator -->
        <div class="tool"><h2>Hash Generator</h2><div class="tool-controls"><select id="hash-type"><option value="md5">MD5</option><option value="sha1">SHA1</option><option value="sha256">SHA256</option><option value="sha512">SHA512</option></select></div><div class="io-container"><textarea id="hash-input" placeholder="Input..."></textarea><div class="output-container"><textarea id="hash-output" readonly placeholder="Output..."></textarea><button class="copy-btn" onclick="copyToClipboard('hash-output')">Copy</button></div></div></div>
        <!-- Hex <=> ASCII -->
        <div class="tool"><h2>Hex <=> ASCII</h2><div class="io-container"><textarea id="hex-input" placeholder="Input (e.g., 'Hello' or '48656c6c6f')"></textarea><div class="output-container"><textarea id="hex-output" readonly placeholder="Output..."></textarea><button class="copy-btn" onclick="copyToClipboard('hex-output')">Copy</button></div></div></div>
        <!-- XOR Cipher -->
        <div class="tool"><h2>XOR Cipher</h2><div class="tool-controls"><label for="xor-key">Key:</label><input type="text" id="xor-key" placeholder="Key..."></div><div class="io-container"><textarea id="xor-input" placeholder="Input..."></textarea><div class="output-container"><textarea id="xor-output" readonly placeholder="Output (Hex)..."></textarea><button class="copy-btn" onclick="copyToClipboard('xor-output')">Copy</button></div></div></div>
        <!-- ROT Ciphers -->
        <div class="tool"><h2>ROT Ciphers</h2><div class="tool-controls"><select id="rot-type"><option value="caesar">Caesar</option><option value="rot13">ROT13</option><option value="rot47">ROT47</option></select><label for="caesar-shift" id="caesar-shift-label">Shift:</label><input type="number" id="caesar-shift" value="3" min="1" max="25"></div><div class="io-container"><textarea id="caesar-input" placeholder="Input..."></textarea><div class="output-container"><textarea id="caesar-output" readonly placeholder="Output..."></textarea><button class="copy-btn" onclick="copyToClipboard('caesar-output')">Copy</button></div></div></div>
        <!-- JWT Decoder -->
        <div class="tool"><h2>JWT Decoder</h2><div class="io-container"><textarea id="jwt-input" placeholder="Paste JWT here..."></textarea><div class="output-container"><textarea id="jwt-output" readonly placeholder="Decoded Header & Payload..."></textarea><button class="copy-btn" onclick="copyToClipboard('jwt-output')">Copy</button></div></div></div>
        <!-- Unix Timestamp -->
        <div class="tool"><h2>Unix Timestamp</h2><div class="io-container"><textarea id="timestamp-input" placeholder="Input (e.g., 1672531200 or 2023-01-01 00:00:00)"></textarea><div class="output-container"><textarea id="timestamp-output" readonly placeholder="Output..."></textarea><button class="copy-btn" onclick="copyToClipboard('timestamp-output')">Copy</button></div></div></div>

        <!-- NEW: Vigenère Cipher -->
        <div class="tool">
            <h2>Vigenère Cipher</h2>
            <div class="tool-controls">
                <label for="vigenere-key">Key:</label><input type="text" id="vigenere-key" placeholder="KEY">
                <select id="vigenere-mode"><option value="encrypt">Encrypt</option><option value="decrypt">Decrypt</option></select>
            </div>
            <div class="io-container"><textarea id="vigenere-input" placeholder="Input..."></textarea><div class="output-container"><textarea id="vigenere-output" readonly placeholder="Output..."></textarea><button class="copy-btn" onclick="copyToClipboard('vigenere-output')">Copy</button></div></div>
        </div>

        <!-- NEW: Number Base Converter -->
        <div class="tool base-converter">
            <h2>Number Base Converter</h2>
            <div class="tool-controls">
                <div class="base-row"><label for="base-dec">Dec:</label><input type="text" class="base-input" id="base-dec" data-base="10"></div>
                <div class="base-row"><label for="base-hex">Hex:</label><input type="text" class="base-input" id="base-hex" data-base="16"></div>
                <div class="base-row"><label for="base-bin">Bin:</label><input type="text" class="base-input" id="base-bin" data-base="2"></div>
                <div class="base-row"><label for="base-oct">Oct:</label><input type="text" class="base-input" id="base-oct" data-base="8"></div>
            </div>
        </div>

        <!-- NEW: Frequency Analysis -->
        <div class="tool">
            <h2>Frequency Analysis</h2>
            <div class="io-container">
                <textarea id="freq-input" placeholder="Paste ciphertext here..."></textarea>
                <div class="output-container"><pre id="freq-output"></pre><button class="copy-btn" onclick="copyToClipboard('freq-output')">Copy</button></div>
            </div>
        </div>

        <!-- NEW: String Escape/Unescape -->
        <div class="tool">
            <h2>String Escape/Unescape</h2>
            <div class="tool-controls">
                 <select id="escape-type">
                    <option value="c_hex">C Hex (\xHH)</option>
                    <option value="url">URL (%HH)</option>
                    <option value="unicode">Unicode (\uHHHH)</option>
                </select>
            </div>
            <div class="io-container"><textarea id="escape-input" placeholder="Input..."></textarea><div class="output-container"><textarea id="escape-output" readonly placeholder="Output..."></textarea><button class="copy-btn" onclick="copyToClipboard('escape-output')">Copy</button></div></div>
        </div>
    
        <!-- NEW: Brainfuck Interpreter -->
        <div class="tool">
            <h2>Brainfuck Interpreter</h2>
            <div class="tool-controls"><button id="bf-run">Execute</button></div>
            <div class="io-container">
                <textarea id="bf-code" placeholder="Brainfuck Code... e.g., ++++++++++[>+++++++>++++++++++>+++>+<<<<-]>++.>+.+++++++..+++.>++.<<+++++++++++++++.>.+++.------.--------.>+.>."></textarea>
                <textarea id="bf-input" placeholder="Program Input (stdin)..." style="height: 60px;"></textarea>
                <div class="output-container"><textarea id="bf-output" readonly placeholder="Program Output (stdout)..."></textarea><button class="copy-btn" onclick="copyToClipboard('bf-output')">Copy</button></div>
            </div>
        </div>
    
         <!-- NEW: Cookie Editor -->
        <div class="tool">
            <h2>Cookie Editor</h2>
            <div class="io-container">
                <textarea id="cookie-input" placeholder="Paste cookie string here... (e.g., key1=value1; key2=value2)"></textarea>
                <div class="output-container"><textarea id="cookie-output" readonly placeholder="Parsed JSON... or new cookie string"></textarea><button class="copy-btn" onclick="copyToClipboard('cookie-output')">Copy</button></div>
            </div>
        </div>

    </div>
</div>

<script>
// --- Core Utilities ---
function copyToClipboard(elementId) { const el = document.getElementById(elementId); const text = el.tagName === 'TEXTAREA' ? el.value : el.innerHTML; navigator.clipboard.writeText(text); const btn = el.closest('.output-container').querySelector('.copy-btn'); const originalText = btn.textContent; btn.textContent = 'Copied!'; btn.classList.add('copied'); setTimeout(() => { btn.textContent = originalText; btn.classList.remove('copied'); }, 1500); }
function debounce(func, delay = 250) { let timeoutId; return (...args) => { clearTimeout(timeoutId); timeoutId = setTimeout(() => { func.apply(this, args); }, delay); }; }

// --- Existing Tool Logic (v2.0) ---
document.getElementById('base64-input').addEventListener('input', debounce(e => { const i = e.target.value, o = document.getElementById('base64-output'); if(i===""){o.value="";return} try{const d=atob(i.trim());o.value=/^[\x00-\x7F]*$/.test(d)?`DECODED:\n${d}`:`ENCODED:\n${btoa(i)}`}catch(e){o.value=`ENCODED:\n${btoa(i)}`}}));
document.getElementById('url-input').addEventListener('input', debounce(e => { const i = e.target.value, o = document.getElementById('url-output'); if(i===""){o.value="";return} try{const d=decodeURIComponent(i.trim().replace(/\+/g,' '));o.value=d!==i?`DECODED:\n${d}`:`ENCODED:\n${encodeURIComponent(i)}`}catch(e){o.value=`ENCODED:\n${encodeURIComponent(i)}`}}));
const hashHandler = debounce(() => {const i=document.getElementById('hash-input').value,t=document.getElementById('hash-type').value,o=document.getElementById('hash-output');if(i){o.value=CryptoJS[t.toUpperCase()](i).toString(CryptoJS.enc.Hex)}else{o.value=''}});
document.getElementById('hash-input').addEventListener('input', hashHandler); document.getElementById('hash-type').addEventListener('change', hashHandler);
document.getElementById('hex-input').addEventListener('input', debounce(e => { const i=e.target.value.trim(),o=document.getElementById('hex-output');if(!i){o.value="";return} if(/^[0-9a-fA-F\s]+$/.test(i)){try{const c=i.replace(/\s/g,'');if(c.length%2!==0){o.value="Invalid hex length";return}let a='';for(let j=0;j<c.length;j+=2){a+=String.fromCharCode(parseInt(c.substr(j,2),16))}o.value=`DECODED (ASCII):\n${a}`}catch(e){}}else{let h='';for(let j=0;j<i.length;j++){h+=i.charCodeAt(j).toString(16).padStart(2,'0')}o.value=`ENCODED (Hex):\n${h}`}}));
const xorHandler=debounce(()=>{const i=document.getElementById('xor-input').value,k=document.getElementById('xor-key').value,o=document.getElementById('xor-output');if(!i||!k){o.value="";return}let r='';for(let j=0;j<i.length;j++){r+=String.fromCharCode(i.charCodeAt(j)^k.charCodeAt(j%k.length))}let h='';for(let j=0;j<r.length;j++){h+=r.charCodeAt(j).toString(16).padStart(2,'0')}o.value=h});
document.getElementById('xor-input').addEventListener('input', xorHandler); document.getElementById('xor-key').addEventListener('input', xorHandler);
const rotHandler=debounce(()=>{const i=document.getElementById('caesar-input').value,t=document.getElementById('rot-type').value,o=document.getElementById('caesar-output');let r='';if(t==='caesar'){const s=parseInt(document.getElementById('caesar-shift').value,10);if(isNaN(s))return;r=i.replace(/[a-zA-Z]/g,c=>{const b=c<'a'?65:97;return String.fromCharCode(((c.charCodeAt(0)-b+s)%26)+b)})}else if(t==='rot13'){r=i.replace(/[a-zA-Z]/g,c=>{const b=c<'a'?65:97;return String.fromCharCode(((c.charCodeAt(0)-b+13)%26)+b)})}else if(t==='rot47'){r=i.replace(/[!-~]/g,c=>String.fromCharCode(33+((c.charCodeAt(0)+47-33)%94)))}o.value=r});
document.getElementById('caesar-input').addEventListener('input', rotHandler); document.getElementById('rot-type').addEventListener('change', rotHandler); document.getElementById('caesar-shift').addEventListener('input', rotHandler); document.getElementById('rot-type').addEventListener('change', ()=>{const isCaesar=document.getElementById('rot-type').value==='caesar';document.getElementById('caesar-shift-label').style.display=isCaesar?'block':'none';document.getElementById('caesar-shift').style.display=isCaesar?'block':'none'; rotHandler();});
document.getElementById('jwt-input').addEventListener('input', debounce(e => { const i=e.target.value.trim(),o=document.getElementById('jwt-output');if(!i){o.value="";return} try{const[h,p,s]=i.split('.');if(!h||!p)throw new Error("Invalid JWT structure");const dH=JSON.parse(atob(h.replace(/-/g,'+').replace(/_/g,'/'))),dP=JSON.parse(atob(p.replace(/-/g,'+').replace(/_/g,'/')));o.value=`// HEADER: ${dH.alg} / ${dH.typ}\n${JSON.stringify(dH,null,2)}\n\n// PAYLOAD\n${JSON.stringify(dP,null,2)}`}catch(e){o.value=`Error: ${e.message}`}}));
document.getElementById('timestamp-input').addEventListener('input', debounce(e => {const i=e.target.value.trim(),o=document.getElementById('timestamp-output');if(!i){o.value="";return}if(/^\d+$/.test(i)){const t=parseInt(i,10),d=new Date(t*(t.toString().length===10?1000:1));o.value=!isNaN(d)?`UTC: ${d.toUTCString()}\nLocal: ${d.toLocaleString()}`:"Invalid Timestamp"}else{try{const d=new Date(i);o.value=!isNaN(d)?`Timestamp (s): ${Math.floor(d.getTime()/1000)}\nTimestamp (ms): ${d.getTime()}`:"Invalid Date String"}catch(e){o.value="Invalid Date String"}}}));

// --- NEW Tool Logic (v3.0) ---

// Vigenère Cipher
const vigenereHandler = debounce(() => {
    const text = document.getElementById('vigenere-input').value;
    const key = document.getElementById('vigenere-key').value.toUpperCase().replace(/[^A-Z]/g, '');
    const mode = document.getElementById('vigenere-mode').value;
    const output = document.getElementById('vigenere-output');
    if (!text || !key) { output.value = ""; return; }
    let result = '';
    for (let i = 0, j = 0; i < text.length; i++) {
        const c = text.charCodeAt(i);
        if (c >= 65 && c <= 90) { // Uppercase
            let shift = key.charCodeAt(j % key.length) - 65;
            if(mode === 'decrypt') shift = -shift;
            result += String.fromCharCode(((c - 65 + shift + 26) % 26) + 65);
            j++;
        } else if (c >= 97 && c <= 122) { // Lowercase
            let shift = key.charCodeAt(j % key.length) - 65;
            if(mode === 'decrypt') shift = -shift;
            result += String.fromCharCode(((c - 97 + shift + 26) % 26) + 97);
            j++;
        } else {
            result += text[i];
        }
    }
    output.value = result;
});
document.getElementById('vigenere-input').addEventListener('input', vigenereHandler);
document.getElementById('vigenere-key').addEventListener('input', vigenereHandler);
document.getElementById('vigenere-mode').addEventListener('change', vigenereHandler);

// Number Base Converter
let isUpdating = false;
document.querySelectorAll('.base-input').forEach(input => {
    input.addEventListener('input', (e) => {
        if (isUpdating) return;
        isUpdating = true;
        const sourceBase = parseInt(e.target.dataset.base, 10);
        const value = e.target.value.trim();
        const num = value === '' ? NaN : parseInt(value, sourceBase);

        if (isNaN(num)) {
            document.querySelectorAll('.base-input').forEach(el => { if (el !== e.target) el.value = ''; });
        } else {
            document.getElementById('base-dec').value = num.toString(10);
            document.getElementById('base-hex').value = num.toString(16).toUpperCase();
            document.getElementById('base-bin').value = num.toString(2);
            document.getElementById('base-oct').value = num.toString(8);
        }
        isUpdating = false;
    });
});

// Frequency Analysis
document.getElementById('freq-input').addEventListener('input', debounce(e => {
    const text = e.target.value;
    const output = document.getElementById('freq-output');
    if (!text) { output.innerHTML = ""; return; }

    const counts = {};
    const filteredText = text.replace(/[^a-zA-Z]/g, '').toUpperCase();
    if (!filteredText) { output.innerHTML = ""; return; }

    for (const char of filteredText) {
        counts[char] = (counts[char] || 0) + 1;
    }

    const sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]);
    const maxCount = sorted[0][1];
  
    let html = '';
    for (const [char, count] of sorted) {
        const percent = (count / filteredText.length * 100).toFixed(2);
        const barWidth = (count / maxCount * 50); // Max 50% width for the bar
        html += `${char} | ${count.toString().padStart(4)} | ${percent.padStart(5)}% <div class="freq-bar" style="width: ${barWidth}%;"></div>\n`;
    }
    output.innerHTML = html;
}));

// String Escape/Unescape
const escapeHandler = debounce(() => {
    const input = document.getElementById('escape-input').value;
    const type = document.getElementById('escape-type').value;
    const output = document.getElementById('escape-output');
    if (!input) { output.value = ""; return; }
  
    // Attempt to unescape first
    let unescaped;
    try {
        if (type === 'c_hex' && /\\x[0-9a-f]{2}/i.test(input)) {
            unescaped = input.replace(/\\x([0-9a-f]{2})/ig, (_, g1) => String.fromCharCode(parseInt(g1, 16)));
        } else if (type === 'url' && /%[0-9a-f]{2}/i.test(input)) {
            unescaped = decodeURIComponent(input);
        } else if (type === 'unicode' && /\\u[0-9a-f]{4}/i.test(input)) {
            unescaped = input.replace(/\\u([0-9a-f]{4})/ig, (_, g1) => String.fromCharCode(parseInt(g1, 16)));
        }
    } catch(e) {/* ignore */}

    if (unescaped && unescaped !== input) {
        output.value = `UNESCAPED:\n${unescaped}`;
    } else { // Escape
        let result = '';
        for (let i = 0; i < input.length; i++) {
            const charCode = input.charCodeAt(i);
            if (type === 'c_hex') result += '\\x' + charCode.toString(16).padStart(2, '0');
            else if (type === 'url') result += '%' + charCode.toString(16).padStart(2, '0');
            else if (type === 'unicode') result += '\\u' + charCode.toString(16).padStart(4, '0');
        }
        output.value = `ESCAPED:\n${result}`;
    }
});
document.getElementById('escape-input').addEventListener('input', escapeHandler);
document.getElementById('escape-type').addEventListener('change', escapeHandler);

// Brainfuck Interpreter
document.getElementById('bf-run').addEventListener('click', () => {
    const code = document.getElementById('bf-code').value.replace(/[^><+\-.,[\]]/g, '');
    const programInput = document.getElementById('bf-input').value;
    const output = document.getElementById('bf-output');
  
    const memory = new Uint8Array(30000);
    let ptr = 0;
    let inputPtr = 0;
    let result = '';
    const maxSteps = 1000000;
    let steps = 0;

    // Pre-calculate jump locations
    const jumpMap = {};
    const stack = [];
    for(let i=0; i<code.length; i++) {
        if (code[i] === '[') stack.push(i);
        else if (code[i] === ']') {
            if (stack.length > 0) {
                const start = stack.pop();
                jumpMap[start] = i;
                jumpMap[i] = start;
            } else { output.value = "Error: Mismatched ']'"; return; }
        }
    }
    if (stack.length > 0) { output.value = "Error: Mismatched '['"; return; }
  
    for (let i = 0; i < code.length && steps < maxSteps; i++, steps++) {
        switch (code[i]) {
            case '>': ptr++; break;
            case '<': ptr--; break;
            case '+': memory[ptr]++; break;
            case '-': memory[ptr]--; break;
            case '.': result += String.fromCharCode(memory[ptr]); break;
            case ',': memory[ptr] = inputPtr < programInput.length ? programInput.charCodeAt(inputPtr++) : 0; break;
            case '[': if (memory[ptr] === 0) i = jumpMap[i]; break;
            case ']': if (memory[ptr] !== 0) i = jumpMap[i]; break;
        }
        if(ptr < 0 || ptr >= memory.length) { output.value = "Error: Pointer out of bounds"; return; }
    }
  
    if (steps >= maxSteps) output.value = `Execution timed out (> ${maxSteps} steps).\nOutput so far:\n${result}`;
    else output.value = result;
});

// Cookie Editor
document.getElementById('cookie-input').addEventListener('input', debounce(e => {
    const input = e.target.value.trim();
    const output = document.getElementById('cookie-output');
    if (!input) { output.value = ""; return; }

    try { // Try parsing as JSON first (for rebuilding a cookie)
        const json = JSON.parse(input);
        output.value = Object.entries(json)
            .map(([key, value]) => `${key}=${typeof value === 'object' ? JSON.stringify(value) : value}`)
            .join('; ');
        output.placeholder = "New cookie string...";
    } catch(e) { // Otherwise, parse as a cookie string
        const cookieObj = Object.fromEntries(input.split(';').map(c => {
            const [key, ...val] = c.trim().split('=');
            return [key, val.join('=')];
        }));
        output.value = JSON.stringify(cookieObj, null, 2);
        output.placeholder = "Parsed JSON...";
    }
}));
</script>
</body>
</html>
```

[执行完毕。]

<br>

<br>

---



**在信息构成的黑暗森林里，每个人都是带枪的猎人。关注 [@bianzhongren](https://t.me/bianzhongren)，让你从猎物变为顶级的掠食者。**

---

### **📢核心阵地 (Our Channels)**

* **Telegram** (资源发布): [点击加入](https://t.me/zzkdm)
* **Github** (技术教程): [前往订阅](https://github.com/zzkdm888)

---

### **🔍资源搜索 (Search Resource)**

* **全网资源搜索01**: https://t.me/+PKsmUwoGckMzOTcx
* **全网资源搜索02**: https://t.me/+4gyZv2aIlZMyYzAx
* **全网资源搜索03**: https://t.me/+ew6WMPpxLnBlMTlh
* **全网资源搜索04**: https://t.me/+MzZlIqxT-dkxYjBh
* **全网资源搜索05**: https://t.me/+1QqSdVTuBKUxNjlh
* **全网资源搜索06**: https://t.me/+uccuaRM2xXBlYTZh
* **全网资源搜索07**: https://t.me/+Tu79GRHczbllMmMx
* **全网资源搜索08**: https://t.me/+igp6CSb59G9mYzQx
* **全网资源搜索09**: https://t.me/+2iLw70FwfL1lZTgx

---

### **⚠️重要声明 (Disclaimer)**

1. **内容用途:** 本人所有平台发布的内容仅供技术学习与信息交流使用。
2. **政治中立:** 本人不参与、不讨论任何政治相关话题，请共同维护纯粹的技术交流环境。
3. **谨防诈骗:** 任何**主动联系你**进行交易或索要信息的人**都是骗子**。请务必提高警惕。
4. **合法合规:** **严禁利用**本项目的任何内容从事任何违反您所在地法律法规的活动。
5. **责任豁免:** 对于因使用或滥用本项目内容而导致的任何直接或间接的风险、损失或法律责任，**本人及本项目概不负责**。

---

### **❤️支持项目 (Support This Project)**

如果本项目对您有帮助，您的支持是项目持续维护和发展的最大动力。

* **USDT(trc20)**: TQqxEfc6Ptyo8zJXFfcVLeJ6AUr3gFC9W1
* **TRX**: TQqxEfc6Ptyo8zJXFfcVLeJ6AUr3gFC9W1
* **USDT(ETH)**: 0x59568a972e5c4e9aedea0ed8b4a8259a9e9953b7
* **USDT(BNB)**: 0x59568a972e5c4e9aedea0ed8b4a8259a9e9953b7
* **USDT(Polygen)**: 0x59568a972e5c4e9aedea0ed8b4a8259a9e9953b7
* **TON**: UQC5uthDJDZXwbkxkoHH8RTostxLgFp7e1WINiKTOEkCUqDv
* **BTC(Taproot)**: bc1prk89wp0x7lvzgdmfmufqqm6h807khezdq6w39e3nxg4yzfskcsfswu9x07
* **BTC(Lagacy)**: 1NwRQD7yjHMsDsQFCjAYkm5QMeciwEj6q
* **BTC(Nested SegWit)**: 372tCpTnemNA6rt2BhPqSm9Yp4jtJdUG3m
* **BTC(Native SegWit)**: bc1qm53xvp5auwr6900228gn77rfureah2tvj86eu9
* **ETH**: 0x59568a972e5c4e9aedea0ed8b4a8259a9e9953b7
  <br>
  **感谢您的每一次支持！ ❤️**
