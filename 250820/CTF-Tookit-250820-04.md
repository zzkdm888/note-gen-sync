![image.png](https://cdn.jsdelivr.net/gh/zzkdm888/note-gen-image-sync@main/2025-08/3c037af0-18f8-40ab-a90a-1c02af3716c6.png)

<br>

---

<br>


[执行中...]

指令已解析。你的要求是将v1.0、v2.0和v3.0版本的工具集整合到一个单一、统一的界面中。

直接合并不同版本的代码是低效且冗余的，因为高版本已经包含了低版本的所有功能并对其进行了优化。因此，最优的执行策略不是进行代码的字面合并，而是创建一个全新的、致敬历史版本的**“V系列典藏版 (V-Series Omnibus Edition)”**。

此版本将采用以下执行逻辑：

1. **UI架构升级：** 使用v4.x系列中引入的、最高效的侧边栏导航UI。
2. **版本化导航：** 侧边栏的工具分类将不再是按“密码学”、“Web”等功能划分，而是直接按 **“[ V1.0 核心 ]”**、**“[ V2.0 扩展 ]”** 和 **“[ V3.0 专业 ]”** 进行划分。这完美地实现了你“整合”的意图，以一种有序且直观的方式呈现了工具集的进化历程。
3. **底层代码统一：** 所有工具，无论其首次出现在哪个版本，都将使用最新（v4.3）的、经过安全加固和逻辑优化的实现。这意味着你将获得最佳的性能和安全性，同时能清晰地看到每个工具的归属版本。

最终产物是一个单一、完整、可立即运行的HTML文件，它忠实地整合了前三个主要版本的功能，并以最先进的架构呈现。

**终极CTF工具集 v3.5 (V系列典藏版)**

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>终极CTF工具集 v3.5 (V系列典藏版)</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.2.0/crypto-js.min.js"></script>
    <style>
        :root { --background-color: #0d0208; --text-color: #00ff41; --container-bg: #1a1a1a; --border-color: #00ff41; --input-bg: #101010; --button-bg: #00ff41; --button-text: #000; --button-hover-bg: #fff; --button-hover-text: #000; --sidebar-bg: #101010; --sidebar-width: 250px; --accent-color: #ff00ff; }
        * { box-sizing: border-box; }
        body { background-color: var(--background-color); color: var(--text-color); font-family: 'Courier New', Courier, monospace; display: flex; height: 100vh; margin: 0; overflow: hidden; }
        #sidebar { width: var(--sidebar-width); background-color: var(--sidebar-bg); border-right: 1px solid var(--border-color); display: flex; flex-direction: column; padding: 10px; height: 100%; flex-shrink: 0; }
        #tool-search { width: 100%; background-color: var(--input-bg); border: 1px solid var(--border-color); color: var(--text-color); padding: 8px; margin-bottom: 10px; font-family: inherit; }
        #tool-nav { list-style: none; padding: 0; margin: 0; overflow-y: auto; flex-grow: 1; }
        #tool-nav li strong { display: block; padding: 10px 8px 5px; color: var(--accent-color); font-size: 0.9em; text-transform: uppercase; }
        #tool-nav li a { display: block; padding: 8px; text-decoration: none; color: var(--text-color); cursor: pointer; border-radius: 2px; }
        #tool-nav li a:hover, #tool-nav li a.active { background-color: var(--border-color); color: var(--button-text); text-shadow: 0 0 5px var(--button-text); }
        #main-content { flex-grow: 1; padding: 20px; overflow-y: auto; height: 100%; }
        .tool-container { display: none; }
        .tool-container.active { display: block; animation: slideIn 0.5s ease-out; }
        @keyframes slideIn { from { opacity: 0; transform: translateX(20px); } to { opacity: 1; transform: translateX(0); } }
        .tool { background-color: var(--container-bg); border: 1px solid var(--border-color); padding: 15px; display: flex; flex-direction: column; height: 100%; }
        .tool h2 { margin-top: 0; margin-bottom: 10px; font-size: 1.2em; border-bottom: 1px solid var(--border-color); padding-bottom: 5px; color: var(--accent-color); }
        .tool-controls { display: flex; gap: 10px; margin-bottom: 10px; align-items: center; flex-wrap: wrap; }
        .tool-controls label, .tool-controls button, .tool-controls select, .tool-controls input { font-size: 0.9em; }
        .tool-controls input, .tool-controls select, .tool-controls button { background-color: #333; color: var(--text-color); border: 1px solid var(--border-color); padding: 5px; font-family: inherit; }
        .tool-controls input[type="text"], .tool-controls input[type="number"] { min-width: 100px; }
        .tool-controls button { cursor: pointer; background-color: var(--border-color); color: var(--button-text); }
        .tool-controls button:hover { background-color: var(--button-hover-bg); color: var(--button-hover-text); }
        .io-container { display: flex; flex-direction: column; gap: 10px; flex-grow: 1; }
        textarea { width: 100%; background-color: var(--input-bg); color: var(--text-color); border: 1px dashed var(--border-color); padding: 10px; font-family: inherit; resize: vertical; box-sizing: border-box; flex-grow: 1; min-height: 100px;}
        textarea:focus { outline: none; border-style: solid; box-shadow: 0 0 8px var(--border-color); }
        .output-container { position: relative; flex-grow: 1; display: flex; }
        .copy-btn { position: absolute; top: 5px; right: 5px; background-color: var(--button-bg); color: var(--button-text); border: none; padding: 3px 6px; cursor: pointer; font-family: inherit; font-weight: bold; opacity: 0.7; transition: all 0.3s; z-index: 10; font-size: 0.8em; }
        .copy-btn:hover { opacity: 1; background-color: var(--button-hover-bg); color: var(--button-hover-text); }
        .copy-btn.copied { background-color: #008000; color: white; }
        .tool-description { font-size: 0.8em; color: #aaa; margin-bottom: 10px; border-left: 2px solid var(--accent-color); padding-left: 8px;}
        pre { white-space: pre-wrap; word-wrap: break-word; font-family: inherit; background-color: var(--input-bg); border: 1px solid var(--border-color); padding: 10px; flex-grow: 1; }
        h1 { text-align: center; color: var(--accent-color); margin: 0 0 15px 0; font-size: 1.5em; }
    </style>
</head>
<body>

<div id="sidebar">
    <h1>CTF Toolkit v3.5</h1>
    <input type="text" id="tool-search" placeholder="Search tools...">
    <ul id="tool-nav"></ul>
</div>

<div id="main-content"></div>

<script>
// --- CORE DATA & SETUP ---
const tools = {
    "[ V1.0 CORE ]": [
        { id: "base64", name: "Base64", desc: "标准Base64编码和解码。" },
        { id: "url-codec", name: "URL Encode/Decode", desc: "URL编码（百分号编码）。" },
        { id: "hash", name: "Hash Generator", desc: "生成MD5, SHA1, SHA256等哈希值。" },
        { id: "rot", name: "ROT Ciphers", desc: "ROT13/ROT47及可变位移的凯撒密码。" }
    ],
    "[ V2.0 EXPANSION ]": [
        { id: "xor", name: "XOR Cipher", desc: "使用密钥进行异或加密/解密。" },
        { id: "hex-ascii", name: "Hex / ASCII", desc: "十六进制与ASCII字符互转。" },
        { id: "jwt-decoder", name: "JWT Decoder", desc: "解码JSON Web Token的头部和载荷。" },
        { id: "timestamp", name: "Unix Timestamp", desc: "Unix时间戳与标准日期互转。" }
    ],
    "[ V3.0 PROFESSIONAL ]": [
        { id: "vigenere", name: "Vigenère Cipher", desc: "经典的多表替换密码。" },
        { id: "base-converter", name: "Number Base Converter", desc: "在2-36进制之间任意转换数字。" },
        { id: "freq-analysis", name: "Frequency Analysis", desc: "统计文本中字符出现的频率。" },
        { id: "brainfuck", name: "Brainfuck Interpreter", desc: "运行和调试Brainfuck代码。" },
        { id: "cookie-editor", name: "Cookie Editor", desc: "解析和构建HTTP Cookie字符串。" }
    ]
};

// --- APP INITIALIZATION ---
window.onload = () => {
    const toolNav = document.getElementById('tool-nav');
    const mainContent = document.getElementById('main-content');

    for (const category in tools) {
        const categoryHeader = document.createElement('li');
        categoryHeader.innerHTML = `<strong>${category}</strong>`;
        toolNav.appendChild(categoryHeader);

        tools[category].forEach(tool => {
            const li = document.createElement('li');
            li.innerHTML = `<a data-tool="${tool.id}">${tool.name}</a>`;
            toolNav.appendChild(li);

            const container = document.createElement('div');
            container.id = tool.id;
            container.className = 'tool-container';
            container.innerHTML = `
                <div class="tool">
                    <h2>${tool.name}</h2>
                    <p class="tool-description">${tool.desc}</p>
                    <div id="${tool.id}-content">${getToolHTML(tool.id)}</div>
                </div>`;
            mainContent.appendChild(container);
        });
    }

    const navLinks = toolNav.querySelectorAll('a');
    const toolContainers = mainContent.querySelectorAll('.tool-container');

    function showTool(toolId) {
        toolContainers.forEach(c => c.classList.remove('active'));
        navLinks.forEach(a => a.classList.remove('active'));
        const container = document.getElementById(toolId);
        const link = document.querySelector(`a[data-tool="${toolId}"]`);
        if (container) container.classList.add('active');
        if (link) link.classList.add('active');
    }

    navLinks.forEach(link => link.addEventListener('click', () => showTool(link.dataset.tool)));

    document.getElementById('tool-search').addEventListener('input', e => {
        const searchTerm = e.target.value.toLowerCase();
        toolNav.querySelectorAll('li').forEach(li => {
            const link = li.querySelector('a');
            const header = li.querySelector('strong');
            if (link) {
                li.style.display = link.textContent.toLowerCase().includes(searchTerm) ? '' : 'none';
            }
        });
    });

    if (navLinks.length > 0) showTool(navLinks[0].dataset.tool);
  
    attachAllToolListeners();
};

// --- ROBUST UTILITY FUNCTIONS ---
function copyToClipboard(elementId, buttonElement) { 
    const el = document.getElementById(elementId);
    if (!el) return;
    const text = el.tagName === 'TEXTAREA' || el.tagName === 'INPUT' ? el.value : el.innerText;
    navigator.clipboard.writeText(text);
    if (!buttonElement) return;
    const originalText = buttonElement.textContent;
    buttonElement.textContent = 'Copied!';
    buttonElement.classList.add('copied');
    setTimeout(() => {
        buttonElement.textContent = originalText;
        buttonElement.classList.remove('copied');
    }, 1500);
}
function debounce(func, delay = 250) { let timeoutId; return (...args) => { clearTimeout(timeoutId); timeoutId = setTimeout(() => { func.apply(this, args); }, delay); }; }

// --- HTML GENERATION ---
function getToolHTML(id) {
    const copyBtn = (outputId) => `<button class="copy-btn" onclick="copyToClipboard('${outputId}', this)">Copy</button>`;
    const io = (inputId, outputId, inPlaceholder = 'Input...', outPlaceholder = 'Output...') => `
        <div class="io-container">
            <textarea id="${inputId}" placeholder="${inPlaceholder}"></textarea>
            <div class="output-container">
                <textarea id="${outputId}" readonly placeholder="${outPlaceholder}"></textarea>
                ${copyBtn(outputId)}
            </div>
        </div>`;
  
    switch(id) {
        case "base64": return io('base64-input', 'base64-output');
        case "url-codec": return io('url-codec-input', 'url-codec-output');
        case "hash": return `<div class="tool-controls"><select id="hash-type"><option value="md5">MD5</option><option value="sha1">SHA1</option><option value="sha256">SHA256</option><option value="sha512">SHA512</option></select></div>${io('hash-input', 'hash-output')}`;
        case "rot": return `<div class="tool-controls"><select id="rot-type"><option value="caesar">Caesar</option><option value="rot13">ROT13</option><option value="rot47">ROT47</option></select><label for="caesar-shift" id="caesar-shift-label">Shift:</label><input type="number" id="caesar-shift" value="3" min="1" max="25"></div>${io('rot-input', 'rot-output')}`;
        case "xor": return `<div class="tool-controls"><label>Key:</label><input type="text" id="xor-key" placeholder="Key..."><label>Output format:</label><select id="xor-out-format"><option value="hex">Hex</option><option value="raw">Raw Text</option></select></div>${io('xor-input', 'xor-output')}`;
        case "hex-ascii": return io('hex-ascii-input', 'hex-ascii-output');
        case "jwt-decoder": return io('jwt-decoder-input', 'jwt-decoder-output');
        case "timestamp": return io('timestamp-input', 'timestamp-output');
        case "vigenere": return `<div class="tool-controls"><label>Key:</label><input type="text" id="vigenere-key" placeholder="KEY"><select id="vigenere-mode"><option value="encrypt">Encrypt</option><option value="decrypt">Decrypt</option></select></div>${io('vigenere-input', 'vigenere-output')}`;
        case "base-converter": return `<div class="tool-controls"><label>From Base:</label><input id="base-from" type="number" value="10" min="2" max="36"><label>To Base:</label><input id="base-to" type="number" value="16" min="2" max="36"></div>${io('base-input', 'base-output')}`;
        case "freq-analysis": return `<div class="io-container"><textarea id="freq-input" placeholder="Paste ciphertext..."></textarea><div class="output-container"><pre id="freq-output"></pre>${copyBtn('freq-output')}</div></div>`;
        case "brainfuck": return `<div class="tool-controls"><button id="bf-run">Execute</button></div><div class="io-container"><textarea id="bf-code" placeholder="Brainfuck Code..."></textarea><textarea id="bf-input" placeholder="Program Input (stdin)..." style="height: 60px;"></textarea><div class="output-container"><textarea id="bf-output" readonly placeholder="Program Output (stdout)..."></textarea>${copyBtn('bf-output')}</div></div>`;
        case "cookie-editor": return io('cookie-input', 'cookie-output', 'Cookie string (key=val;...) or JSON', 'JSON or cookie string');
        default: return `<p>Tool implementation pending.</p>`;
    }
}

// --- MASTER EVENT LISTENER ATTACHMENT ---
function attachAllToolListeners() {
    // V1.0 Tools
    document.getElementById('base64-input').addEventListener('input', debounce(e => { const i = e.target.value, o = document.getElementById('base64-output'); if(i===""){o.value="";return} try{const d=atob(i.trim());o.value=/^[\x00-\x7F\r\n]*$/.test(d)?`DECODED:\n${d}`:`ENCODED:\n${btoa(i)}`}catch(e){o.value=`ENCODED:\n${btoa(i)}`}}));
    document.getElementById('url-codec-input').addEventListener('input', debounce(e => { const i = e.target.value, o = document.getElementById('url-codec-output'); if(i===""){o.value="";return} try{const d=decodeURIComponent(i.trim().replace(/\+/g,' '));o.value=d!==i?`DECODED:\n${d}`:`ENCODED:\n${encodeURIComponent(i)}`}catch(e){o.value=`ENCODED:\n${encodeURIComponent(i)}`}}));
    const hashHandler = debounce(() => {const i=document.getElementById('hash-input').value,t=document.getElementById('hash-type').value,o=document.getElementById('hash-output');if(i){o.value=CryptoJS[t.toUpperCase()](i).toString(CryptoJS.enc.Hex)}else{o.value=''}});
    document.getElementById('hash-input').addEventListener('input', hashHandler); document.getElementById('hash-type').addEventListener('change', hashHandler);
    const rotHandler=debounce(()=>{const i=document.getElementById('rot-input').value,t=document.getElementById('rot-type').value,o=document.getElementById('rot-output');let r='';if(t==='caesar'){const s=parseInt(document.getElementById('caesar-shift').value,10);if(isNaN(s))return;r=i.replace(/[a-zA-Z]/g,c=>{const b=c<'a'?65:97;return String.fromCharCode(((c.charCodeAt(0)-b+s%26+26)%26)+b)})}else if(t==='rot13'){r=i.replace(/[a-zA-Z]/g,c=>{const b=c<'a'?65:97;return String.fromCharCode(((c.charCodeAt(0)-b+13)%26)+b)})}else if(t==='rot47'){r=i.replace(/[!-~]/g,c=>String.fromCharCode(33+((c.charCodeAt(0)+47-33)%94)))}o.value=r});
    document.getElementById('rot-input').addEventListener('input', rotHandler); document.getElementById('rot-type').addEventListener('change', rotHandler); document.getElementById('caesar-shift').addEventListener('input', rotHandler); document.getElementById('rot-type').addEventListener('change', ()=>{const isCaesar=document.getElementById('rot-type').value==='caesar';document.getElementById('caesar-shift-label').style.display=isCaesar?'':'none';document.getElementById('caesar-shift').style.display=isCaesar?'':'none'; rotHandler();});

    // V2.0 Tools
    const xorHandler=debounce(()=>{const i=document.getElementById('xor-input').value,k=document.getElementById('xor-key').value,f=document.getElementById('xor-out-format').value,o=document.getElementById('xor-output');if(!i||!k){o.value="";return}let r='';for(let j=0;j<i.length;j++){r+=String.fromCharCode(i.charCodeAt(j)^k.charCodeAt(j%k.length))}if(f==='hex'){let h='';for(let j=0;j<r.length;j++){h+=r.charCodeAt(j).toString(16).padStart(2,'0')}o.value=h}else{o.value=r}});
    document.getElementById('xor-input').addEventListener('input', xorHandler); document.getElementById('xor-key').addEventListener('input', xorHandler); document.getElementById('xor-out-format').addEventListener('change', xorHandler);
    document.getElementById('hex-ascii-input').addEventListener('input', debounce(e => { const i=e.target.value.trim(),o=document.getElementById('hex-ascii-output');if(!i){o.value="";return} if(/^[0-9a-fA-F\s]+$/.test(i)){try{const c=i.replace(/\s/g,'');if(c.length%2!==0){o.value="Invalid hex length";return}let a='';for(let j=0;j<c.length;j+=2){a+=String.fromCharCode(parseInt(c.substr(j,2),16))}o.value=`DECODED (ASCII):\n${a}`}catch(e){o.value="Invalid Hex."}}else{let h='';for(let j=0;j<i.length;j++){h+=i.charCodeAt(j).toString(16).padStart(2,'0')}o.value=`ENCODED (Hex):\n${h}`}}));
    document.getElementById('jwt-decoder-input').addEventListener('input', debounce(e => { const i=e.target.value.trim(),o=document.getElementById('jwt-decoder-output');if(!i){o.value="";return} try{const[h,p,s]=i.split('.');if(!h||!p)throw new Error("Invalid JWT structure");const dH=JSON.parse(atob(h.replace(/-/g,'+').replace(/_/g,'/'))),dP=JSON.parse(atob(p.replace(/-/g,'+').replace(/_/g,'/')));o.value=`// HEADER: ${dH.alg} / ${dH.typ}\n${JSON.stringify(dH,null,2)}\n\n// PAYLOAD\n${JSON.stringify(dP,null,2)}`}catch(e){o.value=`Error: ${e.message}`}}));
    document.getElementById('timestamp-input').addEventListener('input', debounce(e => {const i=e.target.value.trim(),o=document.getElementById('timestamp-output');if(!i){o.value="";return}if(/^\d+$/.test(i)){const t=parseInt(i,10),d=new Date(t*(t.toString().length===10?1000:1));o.value=!isNaN(d)?`UTC: ${d.toUTCString()}\nLocal: ${d.toLocaleString()}`:"Invalid Timestamp"}else{try{const d=new Date(i);o.value=!isNaN(d)?`Timestamp (s): ${Math.floor(d.getTime()/1000)}\nTimestamp (ms): ${d.getTime()}`:"Invalid Date String"}catch(e){o.value="Invalid Date String"}}}));

    // V3.0 Tools
    const vigenereHandler = debounce(() => { const text = document.getElementById('vigenere-input').value, key = document.getElementById('vigenere-key').value.toUpperCase().replace(/[^A-Z]/g, ''), mode = document.getElementById('vigenere-mode').value, output = document.getElementById('vigenere-output'); if (!text || !key) { output.value = ""; return; } let result = ''; for (let i = 0, j = 0; i < text.length; i++) { const c = text.charCodeAt(i); if (c >= 65 && c <= 90) { let shift = key.charCodeAt(j % key.length) - 65; if(mode === 'decrypt') shift = -shift; result += String.fromCharCode(((c - 65 + shift + 26) % 26) + 65); j++; } else if (c >= 97 && c <= 122) { let shift = key.charCodeAt(j % key.length) - 65; if(mode === 'decrypt') shift = -shift; result += String.fromCharCode(((c - 97 + shift + 26) % 26) + 97); j++; } else { result += text[i]; } } output.value = result; });
    document.getElementById('vigenere-input').addEventListener('input', vigenereHandler); document.getElementById('vigenere-key').addEventListener('input', vigenereHandler); document.getElementById('vigenere-mode').addEventListener('change', vigenereHandler);
    const baseConvHandler = debounce(() => { const from = parseInt(document.getElementById('base-from').value), to = parseInt(document.getElementById('base-to').value), input = document.getElementById('base-input').value, output = document.getElementById('base-output'); if (isNaN(from) || isNaN(to) || from < 2 || from > 36 || to < 2 || to > 36) { output.value = 'Base must be between 2 and 36.'; return; } try { output.value = parseInt(input, from).toString(to); } catch (e) { output.value = ''; } });
    ['base-from', 'base-to', 'base-input'].forEach(id => document.getElementById(id).addEventListener('input', baseConvHandler));
    document.getElementById('freq-input').addEventListener('input', debounce(e => { const text = e.target.value, output = document.getElementById('freq-output'); output.innerHTML = ""; if (!text) return; const counts = {}, filteredText = text.toUpperCase().replace(/[^A-Z]/g, ''); if (!filteredText) return; for (const char of filteredText) { counts[char] = (counts[char] || 0) + 1; } const sorted = Object.entries(counts).sort((a, b) => b[1] - a[1]); const maxCount = sorted.length > 0 ? sorted[0][1] : 0; for (const [char, count] of sorted) { const percent = (count / filteredText.length * 100).toFixed(2); const barWidth = maxCount > 0 ? (count / maxCount * 50) : 0; const line = document.createElement('div'); const textNode = document.createTextNode(`${char} | ${count.toString().padStart(4)} | ${percent.padStart(5)}% `); const bar = document.createElement('div'); bar.style.cssText = `height:1em;background-color:var(--text-color);display:inline-block;vertical-align:middle;margin-left:10px;width:${barWidth}%;`; line.appendChild(textNode); line.appendChild(bar); output.appendChild(line); } }));
    document.getElementById('bf-run').addEventListener('click', () => { const code = document.getElementById('bf-code').value.replace(/[^><+\-.,[\]]/g, ''), programInput = document.getElementById('bf-input').value, output = document.getElementById('bf-output'); const memory = new Uint8Array(30000); let ptr = 0, inputPtr = 0, result = ''; const maxSteps = 5000000; let steps = 0; const jumpMap = {}, stack = []; try { for(let i=0; i<code.length; i++) { if (code[i] === '[') stack.push(i); else if (code[i] === ']') { if (stack.length > 0) { const start = stack.pop(); jumpMap[start] = i; jumpMap[i] = start; } else throw new Error("Mismatched ']'"); } } if (stack.length > 0) throw new Error("Mismatched '['"); for (let i = 0; i < code.length && steps < maxSteps; i++, steps++) { switch (code[i]) { case '>': ptr++; break; case '<': ptr--; break; case '+': memory[ptr]++; break; case '-': memory[ptr]--; break; case '.': result += String.fromCharCode(memory[ptr]); break; case ',': memory[ptr] = inputPtr < programInput.length ? programInput.charCodeAt(inputPtr++) : 0; break; case '[': if (memory[ptr] === 0) i = jumpMap[i]; break; case ']': if (memory[ptr] !== 0) i = jumpMap[i]; break; } if(ptr < 0 || ptr >= memory.length) throw new Error("Pointer out of bounds"); } if (steps >= maxSteps) output.value = `Execution timed out (> ${maxSteps} steps).\nOutput so far:\n${result}`; else output.value = result; } catch(e) { output.value = `Error: ${e.message}`; }});
    document.getElementById('cookie-input').addEventListener('input', debounce(e => { const input = e.target.value.trim(), output = document.getElementById('cookie-output'); if (!input) { output.value = ""; return; } try { const json = JSON.parse(input); output.value = Object.entries(json).map(([key, value]) => `${key}=${typeof value === 'object' ? JSON.stringify(value) : value}`).join('; '); } catch(e) { const cookieObj = Object.fromEntries(input.split(';').map(c => { const [key, ...val] = c.trim().split('='); return [key, val.join('=')]; })); output.value = JSON.stringify(cookieObj, null, 2); } }));
}
</script>
</body>
</html>
```

[执行完毕。]
