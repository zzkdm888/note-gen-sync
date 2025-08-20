![image.png](https://cdn.jsdelivr.net/gh/zzkdm888/note-gen-image-sync@main/2025-08/f6ba4812-180d-4620-87dd-f8a52d566dc9.png)

<br>

---

<br>


[执行中...]

好的，这是一个采用极简黑客风格界面的全面 CTF 工具集。所有功能都封装在一个独立的 HTML 文件中，实现了实时输出和一键复制，并加入了模拟启动序列、扫描线和文字辉光效果，以增强沉浸感。

### 核心特性：

* **极简黑客界面**：纯黑背景，绿色辉光文字，模拟 CRT 扫描线，以及一个闪烁的光标，营造出经典的黑客电影氛围。
* **启动序列动画**：页面加载时会模拟一个系统启动过程，增加代入感。
* **实时交互**：输入命令后，结果会立即显示在下方，整个过程流畅无刷新。
* **隐藏式一键复制**：输出结果旁边会有一个低调的 `[复制]` 标记，点击即可复制内容。
* **全面的工具库**：
  * **编码转换**: Base64, URL, Hex, ASCII, ROT13。
  * **哈希计算**: MD5, SHA-1, SHA-256, SHA-512。
  * **古典密码**: 凯撒密码 (Caesar Cipher), 埃特巴什码 (Atbash Cipher)。
  * **Web 安全**: JWT (JSON Web Token) 解码。
  * **系统命令**: `help` (显示帮助), `clear` (清屏), `banner` (显示欢迎信息)。

### 如何使用：

1. 将下面的代码完整复制并保存为一个 `.html` 文件 (例如 `hacker-toolkit.html`)。
2. 在浏览器中打开这个文件。
3. 等待启动序列完成。
4. 在闪烁的光标后输入命令，例如 `help`，然后按 `Enter` 键查看所有可用工具。

例如，要进行 URL 解码，输入：
`url decode "https%3A%2F%2Fexample.com"`

要计算字符串的 MD5 哈希，输入：
`hash md5 "ctf-challenge"`

---

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CTF HACKER TOOLKIT</title>
    <!-- 引入 Crypto-JS 用于哈希计算 -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/crypto-js/4.1.1/crypto-js.min.js"></script>
    <style>
        :root {
            --main-bg: #000;
            --main-fg: #00FF41;
            --glow-color: rgba(0, 255, 65, 0.75);
            --copy-color: #555;
            --copy-hover: #00FF41;
            --font: 'Consolas', 'Menlo', 'Monaco', 'Courier New', monospace;
        }

        html, body {
            margin: 0;
            padding: 0;
            width: 100%;
            height: 100%;
            background-color: var(--main-bg);
            color: var(--main-fg);
            font-family: var(--font);
            font-size: 16px;
        }

        body::after {
            content: "";
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: repeating-linear-gradient(0deg, rgba(0,0,0,0.4), rgba(0,0,0,0.4) 1px, transparent 1px, transparent 2px);
            pointer-events: none;
            z-index: 9999;
        }

        #terminal {
            padding: 15px;
            box-sizing: border-box;
            height: 100%;
            width: 100%;
            overflow-y: auto;
            text-shadow: 0 0 5px var(--glow-color);
        }
      
        #terminal::-webkit-scrollbar {
            width: 5px;
        }

        #terminal::-webkit-scrollbar-track {
            background: #111;
        }

        #terminal::-webkit-scrollbar-thumb {
            background-color: var(--main-fg);
        }

        #history {
            padding-bottom: 40px; /* Space for the fixed input line */
        }
      
        .line {
            margin-bottom: 5px;
            line-height: 1.5;
            white-space: pre-wrap;
            word-break: break-all;
        }
      
        .result-line {
            display: flex;
            align-items: flex-start;
        }
      
        .result-text {
            flex-grow: 1;
        }
      
        .copy-btn {
            color: var(--copy-color);
            cursor: pointer;
            margin-left: 15px;
            font-weight: bold;
            transition: color 0.2s;
        }
      
        .copy-btn:hover {
            color: var(--copy-hover);
        }
      
        #input-line {
            position: fixed;
            bottom: 0;
            left: 0;
            width: 100%;
            padding: 10px 15px;
            box-sizing: border-box;
            display: flex;
            background-color: var(--main-bg);
        }

        .prompt {
            white-space: nowrap;
        }

        #cli-input {
            flex-grow: 1;
            background: transparent;
            border: none;
            color: inherit;
            font-family: inherit;
            font-size: inherit;
            text-shadow: inherit;
        }

        #cli-input:focus {
            outline: none;
        }

        #cursor {
            display: inline-block;
            width: 10px;
            height: 1.2em;
            background: var(--main-fg);
            animation: blink 1s step-end infinite;
            vertical-align: bottom;
        }

        @keyframes blink {
            from, to { background: transparent }
            50% { background: var(--main-fg); }
        }
    </style>
</head>
<body>

<div id="terminal">
    <div id="history"></div>
    <div id="input-line">
        <span class="prompt">> </span>
        <input type="text" id="cli-input" autocomplete="off" autofocus>
        <span id="cursor"></span>
    </div>
</div>

<script>
    const terminal = document.getElementById('terminal');
    const historyContainer = document.getElementById('history');
    const input = document.getElementById('cli-input');
  
    let commandHistory = [];
    let historyIndex = -1;

    const commands = {
        base64: {
            description: "Base64 编码/解码.",
            usage: "base64 [encode|decode] \"<string>\"",
            execute: ([action, str]) => {
                if (!action || !str) return `用法: ${commands.base64.usage}`;
                try {
                    if (action === 'encode') return btoa(unescape(encodeURIComponent(str)));
                    if (action === 'decode') return decodeURIComponent(escape(atob(str)));
                    return `错误: 未知操作 '${action}'.`;
                } catch (e) {
                    return `解码错误: ${e.message}.`;
                }
            }
        },
        url: {
            description: "URL 编码/解码.",
            usage: "url [encode|decode] \"<string>\"",
            execute: ([action, str]) => {
                if (!action || !str) return `用法: ${commands.url.usage}`;
                try {
                    if (action === 'encode') return encodeURIComponent(str);
                    if (action === 'decode') return decodeURIComponent(str);
                    return `错误: 未知操作 '${action}'.`;
                } catch (e) {
                    return `解码错误: ${e.message}.`;
                }
            }
        },
        hex: {
            description: "Hex 编码/解码.",
            usage: "hex [encode|decode] \"<string>\"",
            execute: ([action, str]) => {
                 if (!action || !str) return `用法: ${commands.hex.usage}`;
                 try {
                     if (action === 'encode') return str.split('').map(c => c.charCodeAt(0).toString(16).padStart(2, '0')).join('');
                     if (action === 'decode') return str.match(/.{1,2}/g).map(hex => String.fromCharCode(parseInt(hex, 16))).join('');
                     return `错误: 未知操作 '${action}'.`;
                 } catch (e) {
                     return `转换错误: ${e.message}.`;
                 }
            }
        },
        ascii: {
            description: "ASCII 字符串与十进制数值互转.",
            usage: "ascii [tochar|todec] \"<values|string>\"",
            execute: ([action, str]) => {
                if (!action || !str) return `用法: ${commands.ascii.usage}`;
                try {
                    if (action === 'todec') return str.split('').map(c => c.charCodeAt(0)).join(' ');
                    if (action === 'tochar') return str.split(/[\s,]+/).map(n => String.fromCharCode(parseInt(n))).join('');
                    return `错误: 未知操作 '${action}'.`;
                } catch(e) {
                    return `转换错误: ${e.message}.`;
                }
            }
        },
        rot13: {
            description: "ROT13 字母替换.",
            usage: "rot13 \"<string>\"",
            execute: ([str]) => {
                if (!str) return `用法: ${commands.rot13.usage}`;
                return str.replace(/[a-zA-Z]/g, c => String.fromCharCode((c <= "Z" ? 90 : 122) >= (c = c.charCodeAt(0) + 13) ? c : c - 26));
            }
        },
        hash: {
            description: "计算哈希值 (md5, sha1, sha256, sha512).",
            usage: "hash [algo] \"<string>\"",
            execute: ([algo, str]) => {
                if (!algo || !str) return `用法: ${commands.hash.usage}`;
                try {
                    const hasher = CryptoJS[algo.toUpperCase()];
                    if (!hasher) return `错误: 不支持的算法 '${algo}'.`;
                    return hasher(str).toString();
                } catch (e) {
                    return `哈希计算错误: ${e.message}.`;
                }
            }
        },
        caesar: {
            description: "凯撒密码.",
            usage: "caesar <shift> \"<string>\"",
            execute: ([shift, str]) => {
                if (!shift || !str) return `用法: ${commands.caesar.usage}`;
                const shiftNum = parseInt(shift, 10);
                if (isNaN(shiftNum)) return "错误: 位移必须是数字。";
                let result = "";
                for (let i = 0; i < str.length; i++) {
                    let char = str[i];
                    if (char.match(/[a-z]/)) {
                        let code = str.charCodeAt(i);
                        char = String.fromCharCode(((code - 97 + shiftNum) % 26 + 26) % 26 + 97);
                    } else if (char.match(/[A-Z]/)) {
                        let code = str.charCodeAt(i);
                        char = String.fromCharCode(((code - 65 + shiftNum) % 26 + 26) % 26 + 65);
                    }
                    result += char;
                }
                return result;
            }
        },
        atbash: {
            description: "埃特巴什码.",
            usage: "atbash \"<string>\"",
            execute: ([str]) => {
                if (!str) return `用法: ${commands.atbash.usage}`;
                return str.replace(/[a-zA-Z]/g, function(c) {
                    var isUpper = c === c.toUpperCase();
                    var start = isUpper ? 'A'.charCodeAt(0) : 'a'.charCodeAt(0);
                    return String.fromCharCode(start + 25 - (c.charCodeAt(0) - start));
                });
            }
        },
        jwt: {
            description: "解码 JWT Token.",
            usage: "jwt decode <token>",
            execute: ([action, token]) => {
                if (action !== 'decode' || !token) return `用法: ${commands.jwt.usage}`;
                try {
                    const [header, payload, signature] = token.split('.');
                    const decodedHeader = JSON.stringify(JSON.parse(atob(header.replace(/-/g, '+').replace(/_/g, '/'))), null, 2);
                    const decodedPayload = JSON.stringify(JSON.parse(atob(payload.replace(/-/g, '+').replace(/_/g, '/'))), null, 2);
                    return `Header:\n${decodedHeader}\n\nPayload:\n${decodedPayload}\n\nSignature: ${signature}`;
                } catch (e) {
                    return `错误: 无效的 JWT Token.`;
                }
            }
        },
        help: {
            description: "显示此帮助信息.",
            usage: "help",
            execute: () => {
                return Object.entries(commands).map(([name, { usage, description }]) => 
                    `${name.padEnd(10)} - ${description}\n           ${usage}`
                ).join('\n\n');
            }
        },
        clear: {
            description: "清空屏幕.",
            usage: "clear",
            execute: () => {
                historyContainer.innerHTML = '';
                return '';
            }
        },
        banner: {
            description: "显示欢迎横幅.",
            usage: "banner",
            execute: () => `CTF HACKER TOOLKIT v1.0\nType 'help' for a list of available commands.`
        }
    };

    const appendLine = (text, isResult = false) => {
        const line = document.createElement('div');
        line.className = 'line';
      
        if (isResult && text) {
            line.classList.add('result-line');
            const textNode = document.createElement('pre');
            textNode.className = 'result-text';
            textNode.textContent = text;
          
            const copyBtn = document.createElement('span');
            copyBtn.className = 'copy-btn';
            copyBtn.textContent = '[复制]';
            copyBtn.onclick = () => {
                navigator.clipboard.writeText(text).then(() => {
                    copyBtn.textContent = '[已复制!]';
                    setTimeout(() => copyBtn.textContent = '[复制]', 1500);
                });
            };
          
            line.appendChild(textNode);
            line.appendChild(copyBtn);

        } else {
            line.innerHTML = text;
        }

        historyContainer.appendChild(line);
        terminal.scrollTop = terminal.scrollHeight;
    };
  
    const processInput = (cmdLine) => {
        appendLine(`> ${cmdLine}`);
        const parts = cmdLine.trim().match(/(?:[^\s"]+|"[^"]*")+/g) || [];
        if (parts.length === 0) return;

        const command = parts[0].toLowerCase();
        const args = parts.slice(1).map(arg => arg.startsWith('"') && arg.endsWith('"') ? arg.slice(1, -1) : arg);

        if (commands[command]) {
            const result = commands[command].execute(args);
            if (result) {
                appendLine(result, true);
            }
        } else {
            appendLine(`command not found: ${command}`);
        }
    };
  
    input.addEventListener('keydown', e => {
        if (e.key === 'Enter') {
            const command = input.value;
            if(command.trim() !== '') {
                commandHistory.push(command);
                historyIndex = commandHistory.length;
                processInput(command);
            }
            input.value = '';
        } else if (e.key === 'ArrowUp') {
            e.preventDefault();
            if (historyIndex > 0) {
                historyIndex--;
                input.value = commandHistory[historyIndex];
            }
        } else if (e.key === 'ArrowDown') {
            e.preventDefault();
            if (historyIndex < commandHistory.length - 1) {
                historyIndex++;
                input.value = commandHistory[historyIndex];
            } else {
                historyIndex = commandHistory.length;
                input.value = '';
            }
        }
    });

    // Make the whole terminal focus the input on click
    terminal.addEventListener('click', () => {
        input.focus();
    });

    // Boot sequence
    const bootSequence = [
        { text: 'Booting kernel...', delay: 200 },
        { text: 'Initializing modules...', delay: 300 },
        { text: 'Mounting file systems... [OK]', delay: 500 },
        { text: 'Establishing secure connection... [ENCRYPTED]', delay: 400 },
        { text: '', delay: 200 },
        { text: commands.banner.execute(), delay: 100 }
    ];

    let delay = 0;
    bootSequence.forEach(item => {
        delay += item.delay;
        setTimeout(() => appendLine(item.text), delay);
    });

</script>
</body>
</html>
```

[执行完毕。]
