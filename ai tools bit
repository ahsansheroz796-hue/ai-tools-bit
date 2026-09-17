
The user is asking "can you create HTML code" - a very open-ended request. I should say yes and provide something useful. Since they didn't specify what they want, I should give a nice example and ask what they'd like. Let me create a decent, self-contained HTML page demo that's visually appealing and functional, then ask for specifics.

Let me make a clean, modern single-file HTML page — maybe a simple interactive demo like a todo list or a profile card. A todo list is practical and shows HTML/CSS/JS together. Let me do that, keeping it reasonably concise but polished.

Actually, let me keep it moderate in length — a nice todo app with localStorage would be good but maybe overkill. I'll do a clean, styled page with a bit of interactivity. Let me write it well.

I'll write the code in an artifact-style code block. Since this is a chat, I'll just output the code block.

Let me make a small, self-contained todo app:

HTML structure

CSS with modern styling, dark-ish or light theme

JS for add/delete/toggle/complete, with localStorage

Keep it readable. Then ask what they actually want.

Here's a complete, ready-to-run HTML document for a modern Todo app with a clean, responsive interface and local storage support.

html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Todo App</title>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: system-ui, -apple-system, "Segoe UI", Roboto, sans-serif;
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      padding: 40px 16px;
    }

    .app {
      background: #fff;
      width: 100%;
      max-width: 480px;
      border-radius: 16px;
      box-shadow: 0 20px 50px rgba(0, 0, 0, 0.25);
      overflow: hidden;
    }

    header {
      padding: 28px 24px 20px;
      border-bottom: 1px solid #eee;
    }

    h1 {
      font-size: 1.5rem;
      color: #2d3748;
    }

    .subtitle {
      font-size: 0.85rem;
      color: #a0aec0;
      margin-top: 4px;
    }

    .input-row {
      display: flex;
      gap: 8px;
      padding: 20px 24px;
    }

    input[type="text"] {
      flex: 1;
      padding: 12px 14px;
      font-size: 0.95rem;
      border: 2px solid #e2e8f0;
      border-radius: 10px;
      outline: none;
      transition: border-color 0.2s;
    }

    input[type="text"]:focus {
      border-color: #667eea;
    }

    button.add {
      padding: 12px 20px;
      font-size: 0.95rem;
      font-weight: 600;
      color: #fff;
      background: #667eea;
      border: none;
      border-radius: 10px;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
    }

    button.add:hover { background: #5568d3; }
    button.add:active { transform: scale(0.96); }

    ul {
      list-style: none;
      padding: 0 24px 24px;
      max-height: 50vh;
      overflow-y: auto;
    }

    li {
      display: flex;
      align-items: center;
      gap: 12px;
      padding: 14px 0;
      border-bottom: 1px solid #f0f0f0;
      animation: slideIn 0.25s ease;
    }

    @keyframes slideIn {
      from { opacity: 0; transform: translateY(-6px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    li input[type="checkbox"] {
      width: 18px;
      height: 18px;
      cursor: pointer;
      accent-color: #667eea;
      flex-shrink: 0;
    }

    li span {
      flex: 1;
      color: #2d3748;
      font-size: 0.95rem;
      word-break: break-word;
      transition: color 0.2s;
    }

    li.done span {
      text-decoration: line-through;
      color: #cbd5e0;
    }

    .delete {
      background: none;
      border: none;
      color: #cbd5e0;
      font-size: 1.3rem;
      line-height: 1;
      cursor: pointer;
      padding: 0 4px;
      transition: color 0.2s;
    }

    .delete:hover { color: #e53e3e; }

    .empty {
      text-align: center;
      color: #cbd5e0;
      font-size: 0.9rem;
      padding: 30px 0;
    }

    footer {
      padding: 14px 24px;
      background: #fafafa;
      border-top: 1px solid #eee;
      font-size: 0.8rem;
      color: #a0aec0;
      display: flex;
      justify-content: space-between;
    }

    footer button {
      background: none;
      border: none;
      color: #a0aec0;
      font-size: 0.8rem;
      cursor: pointer;
      text-decoration: underline;
    }

    footer button:hover { color: #667eea; }
  </style>
</head>
<body>

  <div class="app">
    <header>
      <h1>📝 My Todos</h1>
      <p class="subtitle">Stay organized, get things done.</p>
    </header>

    <div class="input-row">
      <input type="text" id="taskInput" placeholder="What needs to be done?" autocomplete="off">
      <button class="add" id="addBtn">Add</button>
    </div>

    <ul id="taskList"></ul>

    <footer>
      <span id="counter">0 tasks</span>
      <button id="clearBtn">Clear completed</button>
    </footer>
  </div>

  <script>
    const input    = document.getElementById('taskInput');
    const addBtn   = document.getElementById('addBtn');
    const list     = document.getElementById('taskList');
    const counter  = document.getElementById('counter');
    const clearBtn = document.getElementById('clearBtn');

    // Load saved tasks from localStorage
    let tasks = JSON.parse(localStorage.getItem('my-tasks') || '[]');

    function save() {
      localStorage.setItem('my-tasks', JSON.stringify(tasks));
    }

    function render() {
      list.innerHTML = '';

      if (tasks.length === 0) {
        list.innerHTML = '<li class="empty">Nothing here yet. Add a task above! ✨</li>';
      } else {
        tasks.forEach((task, index) => {
          const li = document.createElement('li');
          if (task.done) li.classList.add('done');

          // Checkbox
          const checkbox = document.createElement('input');
          checkbox.type = 'checkbox';
          checkbox.checked = task.done;
          checkbox.addEventListener('change', () => {
            tasks[index].done = checkbox.checked;
            save();
            render();
          });

          // Text
          const span = document.createElement('span');
          span.textContent = task.text;

          // Delete button
          const del = document.createElement('button');
          del.className = 'delete';
          del.textContent = '×';
          del.title = 'Delete task';
          del.addEventListener('click', () => {
            tasks.splice(index, 1);
            save();
            render();
          });

          li.append(checkbox, span, del);
          list.appendChild(li);
        });
      }

      const remaining = tasks.filter(t => !t.done).length;
      counter.textContent = `${remaining} task${remaining === 1 ? '' : 's'} left`;
    }

    function addTask() {
      const text = input.value.trim();
      if (!text) return;

      tasks.push({ text, done: false });
      input.value = '';
      save();
      render();
      input.focus();
    }

    addBtn.addEventListener('click', addTask);

    input.addEventListener('keydown', (e) => {
      if (e.key === 'Enter') addTask();
    });

    clearBtn.addEventListener('click', () => {
      tasks = tasks.filter(t => !t.done);
      save();
      render();
    });

    // Initial render
    render();
  </script>

</body>
</html>
Todo App: Core Features & Interactions
Here’s a quick tour of what you can do with this page.

Add tasks: Type into the input field and press Enter or click the Add button. The new task appears at the top of the list.

Mark as complete: Check the checkbox next to a task. The text gets a strikethrough and fades, and the remaining task counter updates.

Delete tasks: Click the × button on any task to remove it from the list.

Clear completed: Use the "Clear completed" link at the bottom to remove all finished tasks at once.

Persistence: All tasks are saved to your browser’s localStorage, so they stay even after you refresh or close the page.

Empty state: If there are no tasks, the list shows a friendly message to encourage adding one.

Optimization Tip: You can change the app’s color scheme by editing the gradient in the body style, and adjust the storage key 'my-tasks' in the script if you want multiple lists. The code is self-contained and needs no external libraries.

Create html code for my website including this website is calculator image compressor pdf compressor advance ai tools and much more or make this website professional and advance
The user wants an HTML code for a website that includes calculator, image compressor, PDF compressor, advanced AI tools, and much more. They want it professional and advanced.

I should create a single-page HTML file with a modern, professional design. I'll include:

A landing page with hero section

Tool cards grid featuring: Calculator, Image Compressor, PDF Compressor, AI Tools, and more

Working calculator (functional)

Working image compressor (using canvas API - client-side)

PDF compressor (client-side is tricky; I can use a library like pdf-lib from CDN, or simulate. Actually I could use pdf-lib to re-save PDF which can reduce size. Let me use pdf-lib from CDN)

AI tools section — could integrate with an API, but without a key, I can make a UI that's ready for API integration. Or a simple local "AI" like text summarizer/tools. I'll make a UI with a note about API key.

More tools: QR code generator, color picker, text tools, etc.

Let me build this as a single HTML file with:

Modern dark/light theme

Responsive nav

Hero

Tools grid

Modal-based tool panels

Functional calculator

Functional image compressor (canvas-based, quality slider, download)

Functional PDF compressor (pdf-lib — re-save with compression, though pdf-lib doesn't really compress images. Alternative: I could just re-save. Let me be honest in the UI that it does structural optimization. Actually pdf-lib can load and save, which may reduce size slightly. I'll present it as a PDF optimizer.)

Hmm, but they want "PDF compressor". I'll implement with pdf-lib load + save with objectsPerTick, and show size reduction. It's genuine — removing unused objects can reduce size.

QR code generator — I could use an API or a library. Using a CDN library like qrcode.js. Let me include it via CDN: https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js — actually the package is qrcodejs on jsdelivr? Let me use https://cdn.jsdelivr.net/npm/qrcode-generator@1.4.4/qrcode.js. Hmm, risky. Alternative: generate QR with a canvas implementation... too long.

Actually, I can use an API-free approach or just use api.qrserver.com image. That requires internet but is simple: https://api.qrserver.com/v1/create-qr-code/?size=200x200&data=.... That works and is simple. But it's an external service. I'll use it and note it.

Actually let me keep it simpler and more reliable. I'll include a good set of tools:

Calculator (fully functional, advanced with keyboard support)

Image Compressor (canvas, quality + max width, before/after size)

PDF Compressor (pdf-lib)

QR Code Generator (via api.qrserver.com)

AI Tools (UI ready with API integration placeholder — text summarizer, code explainer, etc. using OpenAI-compatible endpoint where user enters key) — I'll make it functional-ish with a settings for API key stored in localStorage.

Unit Converter / Color Picker / Password Generator — more "much more"

Let me add:

Password Generator (functional)

Unit Converter (functional)

Color Picker / Palette (functional)

Word Counter (functional)

That gives a rich toolset.

Design: dark theme with glassmorphism, gradient accents, smooth animations, professional.

Let me write clean code.

Structure:

html
<!DOCTYPE html>
<html lang="en">
<head>
  meta, title, styles
</head>
<body>
  <header nav>
  <main>
    <section hero>
    <section tools grid>
    <section features>
    <section about/stats>
    <footer>
  </main>
  <!-- Modals for each tool -->
  <script src="pdf-lib cdn"></script>
  <script>app logic</script>
</body>
</html>
I'll use a modal system where clicking a tool card opens a modal with the tool UI.

Let me be careful about size — this will be long but that's fine.

CSS: use CSS variables, dark theme by default with light toggle maybe. Let's keep dark + a theme toggle.

Let me write it.

Key CSS:

css
:root {
  --bg: #0b0f19;
  --bg-2: #111827;
  --card: rgba(255,255,255,0.04);
  --border: rgba(255,255,255,0.08);
  --text: #e5e7eb;
  --muted: #94a3b8;
  --primary: #6366f1;
  --primary-2: #8b5cf6;
  --accent: #22d3ee;
  --success: #10b981;
  --danger: #ef4444;
  --radius: 16px;
}
Light theme via [data-theme="light"].

Let me now write the tools.

Calculator: advanced — supports +, -, ×, ÷, %, ±, decimal, clear, backspace, keyboard input. Display with expression history.

I'll implement with a state: current, previous, operator, and an expression display.

js
let calc = { current: '0', previous: null, operator: null, justEvaluated: false };
Image Compressor: file input, preview, quality slider, max width slider, output size, download button. Uses canvas.toBlob with quality.

PDF Compressor: pdf-lib. Load PDF, then save with useObjectStreams: true which compresses. Show before/after.

Actually pdf-lib's save({ useObjectStreams: true }) is default true. It may help. Also I can remove metadata. Let's do it.

QR Code: input text, size, generate via api.qrserver.com, download image.

AI Tools: A text area + task select (summarize, rewrite, explain, translate-ish, generate ideas). Uses fetch to an OpenAI-compatible endpoint. User enters API key + base URL + model in settings, saved in localStorage. If no key, show demo message. This makes it "advance AI tools" ready.

Password Generator: length slider, options, generate, copy.

Unit Converter: length/weight/temperature. Maybe keep simple with categories.

Word/Text Counter: count words, chars, sentences, reading time, plus case conversion buttons.

That's a lot. Let me maybe trim to keep the code manageable but still rich:

Tools:

Calculator

Image Compressor

PDF Compressor

AI Assistant

QR Generator

Password Generator

Unit Converter

Text Tools

8 tools. Good.

Let me write the modal system.

js
function openTool(id){ ... }
Each tool has a <div class="modal" id="modal-calc"> etc.

Let me write out the code now.

I'll be careful with HTML escaping inside JS template strings.

Let me write.

For toast notifications, I'll add a simple toast function.

Let me start writing.

html
<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>NexusTools — Free Online Calculator, Image & PDF Compressor, AI Tools</title>
<meta name="description" content="...">
<style> ... </style>
</head>
<body>
...
</body>
</html>
CSS — let me write it well.

css
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
  font-family: 'Inter', system-ui, -apple-system, 'Segoe UI', Roboto, sans-serif;
  background: var(--bg);
  color: var(--text);
  line-height:1.6;
  -webkit-font-smoothing:antialiased;
  overflow-x:hidden;
}
Background glow effects with fixed pseudo elements.

Nav:

css
.nav{position:sticky;top:0;z-index:50;backdrop-filter:blur(16px);background:rgba(11,15,25,.72);border-bottom:1px solid var(--border)}
.nav-inner{max-width:1200px;margin:0 auto;padding:14px 20px;display:flex;align-items:center;gap:24px}
Hero with big gradient title.

Tools grid: grid-template-columns:repeat(auto-fill,minmax(260px,1fr)).

Tool card: hover lift, icon with gradient background.

Modal: fixed overlay, centered panel, scroll.

Let me write everything out now carefully.

For the calculator display, I'll use a monospace-ish font.

Now writing the JS.

Calculator logic:

js
const calcState = { current:'0', previous:null, op:null, resetNext:false };

function calcUpdate(){
  document.getElementById('calcCurrent').textContent = calcState.current;
  document.getElementById('calcExpr').textContent =
    (calcState.previous !== null ? calcState.previous + ' ' + (calcState.op||'') : '');
}

function calcInput(d){
  if(calcState.resetNext){ calcState.current = '0'; calcState.resetNext = false; }
  if(d === '.'){ if(!calcState.current.includes('.')) calcState.current += '.'; }
  else {
    if(calcState.current === '0') calcState.current = d;
    else calcState.current += d;
  }
  if(calcState.current.length > 16) calcState.current = calcState.current.slice(0,16);
}
Hmm, careful with leading zeros.

js
function calcOp(op){
  const cur = parseFloat(calcState.current);
  if(calcState.previous !== null && calcState.op && !calcState.resetNext){
    const res = calcCompute(calcState.previous, cur, calcState.op);
    calcState.current = String(res);
    calcState.previous = res;
  } else {
    calcState.previous = cur;
  }
  calcState.op = op;
  calcState.resetNext = true;
}
Hmm, when pressing operator after pressing equals, previous should be current.

Let me restructure: store previous as a number.

js
function calcOp(op){
  const cur = parseFloat(calcState.current) || 0;
  if(calcState.op && calcState.previous !== null && !calcState.resetNext){
    const res = calcCompute(calcState.previous, cur, calcState.op);
    calcState.current = fmt(res);
    calcState.previous = res;
  } else {
    calcState.previous = cur;
  }
  calcState.op = op;
  calcState.resetNext = true;
  calcUpdate();
}
Wait if resetNext is true and user presses another operator, we just change the operator. With the code above, calcState.op is truthy and previous not null but resetNext is true so it goes to else and sets previous = cur (which is the result). That's fine, then op changes. OK good.

js
function calcEquals(){
  if(calcState.op === null || calcState.previous === null) return;
  const cur = parseFloat(calcState.current) || 0;
  const res = calcCompute(calcState.previous, cur, calcState.op);
  calcState.current = fmt(res);
  calcState.previous = null;
  calcState.op = null;
  calcState.resetNext = true;
  calcUpdate();
}
calcCompute:

js
function calcCompute(a,b,op){
  switch(op){
    case '+': return a+b;
    case '−': return a-b;
    case '×': return a*b;
    case '÷': return b===0 ? NaN : a/b;
    case '%': return a % b;
    default: return b;
  }
}
fmt: handle NaN, Infinity, round to reasonable precision.

js
function fmt(n){
  if(!isFinite(n)) return 'Error';
  let s = parseFloat(n.toPrecision(12)).toString();
  return s;
}
Also handle 'Error' state — if current is 'Error', reset on next input.

Percent button: maybe just treat as modulo, or convert to /100. I'll make % work as modulo when in an operation, but simpler: make it "percent of previous". Eh. Let me just make '%' an operator meaning modulo. Actually most calculators use % as percentage. Let me keep it simple and label it '%' doing modulo — fine for a demo. Hmm, but users may find that odd.

Alternative: make the button "±" for sign toggle and have % do percentage. Let me do:

± toggles sign

% divides current by 100 (if no pending op) or computes percentage of previous.

Simplest robust: % → current = current/100, display. Let me do that and also handle when there's a pending op: percent of previous. I'll do: if previous !== null, current = previous * current/100, else current = current/100.

OK.

Backspace: remove last char.

AC: reset all.

Keyboard support when calculator modal is open.

Now, Image Compressor:

js
let imgFile = null, imgOriginalSize = 0, imgResultBlob = null;
On file select: show preview, original size, run compression with current settings.

Compress function:

js
function compressImage(){
  if(!imgFile) return;
  const img = new Image();
  const url = URL.createObjectURL(imgFile);
  img.onload = () => {
    const maxW = parseInt(maxWidthInput.value) || 1920;
    let w = img.width, h = img.height;
    if(w > maxW){ h = Math.round(h * maxW / w); w = maxW; }
    const canvas = document.createElement('canvas');
    canvas.width = w; canvas.height = h;
    const ctx = canvas.getContext('2d');
    ctx.imageSmoothingQuality = 'high';
    // white bg for transparent png -> jpeg
    ctx.fillStyle = '#fff'; // only if output jpeg
    ctx.fillRect(0,0,w,h);
    ctx.drawImage(img, 0, 0, w, h);
    const quality = parseInt(qualityInput.value)/100;
    const type = outputFormat.value; // 'image/jpeg' | 'image/webp'
    canvas.toBlob(blob => {
      URL.revokeObjectURL(url);
      if(!blob) return;
      imgResultBlob = blob;
      // update UI
    }, type, quality);
  };
  img.src = url;
}
Good.

PDF compressor with pdf-lib:

js
const { PDFDocument } = PDFLib;
const bytes = await file.arrayBuffer();
const pdfDoc = await PDFDocument.load(bytes, { ignoreEncryption: true });
// remove metadata
pdfDoc.setTitle(''); ...
const out = await pdfDoc.save({ useObjectStreams: true });
Then create Blob with type application/pdf.

Note: pdf-lib may actually increase size sometimes. I'll show both and if bigger, tell user original is already optimized and offer the original download. Good honest UX.

AI Assistant: I'll build a UI with provider settings (API key, base URL, model) stored in localStorage, a prompt textarea, task presets, and a response area. On submit, fetch to ${baseUrl}/chat/completions with the key.

Default baseUrl: https://api.openai.com/v1, model gpt-4o-mini.

If no key, show a message explaining how to set it up, and show a "demo mode" response that's clearly labeled. Actually let me just show a clear message rather than fake AI output. Hmm, but the user wants it to look functional. I'll show a nice message with instructions. And I'll include a "Demo" response that explains it's a demo. Let's keep honest: show an error/instruction card.

Actually I'll make it: if no key, show a friendly notice in the output area explaining setup. That's professional.

QR Generator: uses api.qrserver.com. Input text, size select, generate → img src. Download via fetch blob or just link with download attribute (cross-origin may not download properly; I'll fetch as blob then download).

CORS on api.qrserver.com — it does allow CORS I believe. If fetch fails, fall back to opening in new tab.

Password generator: straightforward.

Unit converter: categories length, weight, temperature, area... Let me do length, weight, temperature, and data. Simple.

Text tools: textarea with live stats and buttons (uppercase, lowercase, title case, remove extra spaces, reverse, copy, clear).

OK. Let me also add a search/filter for tools? Nice touch. Yes — a search input that filters tool cards.

Let me write the full code.

I need to be mindful: this is going to be ~1200 lines. That's OK.

Let me write.

Also add a footer with links, and a "back to top" maybe.

Let me write the HTML for tool cards with data attributes.

html
<article class="tool-card" data-tool="calc" data-tags="calculator math numbers">
  <div class="tool-icon" style="--i1:#6366f1;--i2:#8b5cf6">🧮</div>
  <h3>Calculator</h3>
  <p>Fast, keyboard-friendly scientific calculator with memory and history.</p>
  <span class="tool-link">Open tool →</span>
</article>
I'll use emoji icons for simplicity, styled in gradient boxes. Or SVG. Emoji is fine and lightweight.

Actually for a "professional" look, inline SVG icons would be better. But emoji in a gradient rounded square looks quite good and modern. I'll go with emoji but styled nicely.

Hmm, let me use SVG icons for the main features to look more premium. That's a lot of SVG code though. I'll use emoji — it's pragmatic and still looks clean.

Let me write it now.

For the modal, structure:

html
<div class="modal-overlay" id="modal-calc" data-modal>
  <div class="modal">
    <div class="modal-head">
      <div class="modal-title"><span class="mi">🧮</span> Calculator</div>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body"> ... </div>
  </div>
</div>
JS: document.querySelectorAll('[data-tool]') click → open modal by id modal-${tool}.

Close on overlay click, close button, Escape.

Now, calculators etc. need to be initialized once. Since they're in the DOM from the start, I can just bind everything on load.

Let's write.

CSS for modal:

css
.modal-overlay{position:fixed;inset:0;background:rgba(3,6,15,.75);backdrop-filter:blur(6px);display:none;align-items:center;justify-content:center;padding:20px;z-index:100}
.modal-overlay.open{display:flex}
.modal{background:var(--bg-2);border:1px solid var(--border);border-radius:20px;width:100%;max-width:520px;max-height:90vh;display:flex;flex-direction:column;overflow:hidden;animation:pop .25s ease}
Add animation.

Modal body scrollable.

Let me now write out the full file.

For number inputs and range sliders, style them.

I'll write the code now in full.

One more consideration — the PDFLib global from the CDN. Script: https://unpkg.com/pdf-lib@1.17.1/dist/pdf-lib.min.js. That exposes PDFLib. Good.

I should handle the case where the CDN fails to load (offline). I'll check typeof PDFLib === 'undefined' and show a message.

Alright, writing.

Let me carefully write the JS for each tool.

I'll wrap everything in an IIFE or DOMContentLoaded.

Let's go.

For the toast:

js
function toast(msg, type){
  const t = document.createElement('div');
  t.className = 'toast' + (type ? ' ' + type : '');
  t.textContent = msg;
  document.getElementById('toasts').appendChild(t);
  setTimeout(()=>{ t.classList.add('show'); }, 10);
  setTimeout(()=>{ t.classList.remove('show'); setTimeout(()=>t.remove(), 300); }, 2600);
}
OK writing now.

Also need formatBytes.

Let me finalize the tools list and their modal contents.

I'm going to write it now for real.

Regarding the AI tool — let me build a clean chat-ish interface:

Settings row (collapsible): API Key, Base URL, Model, Save button

Task select: Summarize / Rewrite / Explain / Translate to English / Generate ideas / Fix grammar / Custom

Input textarea

Run button

Output area

Fetch:

js
const res = await fetch(baseUrl.replace(/\/$/,'') + '/chat/completions', {
  method:'POST',
  headers:{'Content-Type':'application/json','Authorization':'Bearer '+key},
  body: JSON.stringify({ model, messages:[{role:'system',content:sys},{role:'user',content:prompt}], temperature:0.7 })
});
Handle errors.

Good. Write it.

Let me count the CSS carefully to keep it organized.

Writing final answer now.

For the hero, I'll add a search bar that filters tools and scrolls to the grid.

Also stats: "8+ Tools", "100% Free", "No signup", "Privacy-first — files never leave your device" (true for image/pdf compression since it's client-side).

Great selling point. Let me highlight that.

Now writing.

Final structure of body:

html
<div class="bg-glow"></div>
<header class="nav">...</header>
<main>
  <section class="hero">...</section>
  <section class="tools" id="tools">...</section>
  <section class="features" id="features">...</section>
  <section class="cta">...</section>
</main>
<footer>...</footer>
<div id="toasts"></div>
<!-- modals -->
Let me write it all.

I'll keep the feature section compact.

Code time.

For the nav, add mobile-friendly: just logo + links that hide on small screens, plus theme toggle.

Alright.

Let me write out the complete HTML.

Note on the % button in the calculator — I'll use %.

Calculator buttons layout (4 columns):

text
AC  ⌫  %  ÷
7   8  9  ×
4   5  6  −
1   2  3  +
±   0  .  =
That's 5 rows × 4 = 20 buttons.

Let me write the button HTML with data attributes:

html
<button class="cbtn" data-num="7">7</button>
<button class="cbtn op" data-op="÷">÷</button>
<button class="cbtn fn" data-fn="ac">AC</button>
<button class="cbtn fn" data-fn="back">⌫</button>
<button class="cbtn fn" data-fn="pct">%</button>
<button class="cbtn fn" data-fn="sign">±</button>
<button class="cbtn eq" data-fn="eq">=</button>
JS: delegate clicks on the keypad container.

Good.

Now writing for real. I'll produce the final answer with a brief intro and the code.

One thing: the response should probably be mostly the code. I'll add a short intro and a short "what's inside" note.

Let me write.

For unit converter data:

js
const units = {
  length: { name:'Length', base:'m', units:{ 'Meter (m)':1, 'Kilometer (km)':1000, 'Centimeter (cm)':0.01, 'Millimeter (mm)':0.001, 'Mile (mi)':1609.344, 'Yard (yd)':0.9144, 'Foot (ft)':0.3048, 'Inch (in)':0.0254 } },
  weight: { name:'Weight', base:'kg', units:{ 'Kilogram (kg)':1, 'Gram (g)':0.001, 'Milligram (mg)':1e-6, 'Metric ton (t)':1000, 'Pound (lb)':0.45359237, 'Ounce (oz)':0.028349523125 } },
  data: { name:'Data', base:'MB', units:{ 'Byte (B)':1e-6, 'Kilobyte (KB)':0.001, 'Megabyte (MB)':1, 'Gigabyte (GB)':1000, 'Terabyte (TB)':1e6 } },
  temperature: special
};
Temperature needs special handling. I'll handle it separately.

OK, writing.

Let me just make temperature convert to Celsius then out.

js
function convertTemp(v, from, to){
  let c;
  if(from==='c') c=v; else if(from==='f') c=(v-32)*5/9; else c=v-273.15;
  if(to==='c') return c; if(to==='f') return c*9/5+32; return c+273.15;
}
Fine.

Now write everything.

I'll write the final code.

Here's a complete, ready-to-run HTML document for your professional online tools hub, featuring a calculator, image and PDF compressors, AI assistant, and more. You can open it directly in any modern browser.

html
<!DOCTYPE html>
<html lang="en" data-theme="dark">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>NexusTools — Free Online Calculator, Image Compressor, PDF Compressor & AI Tools</title>
<meta name="description" content="A professional suite of free online tools: advanced calculator, image compressor, PDF compressor, AI assistant, QR generator, password generator, unit converter and text utilities. 100% browser-based and private.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet">
<style>
/* ============ THEME TOKENS ============ */
:root{
  --bg:#0b0f19;
  --bg-2:#111827;
  --bg-3:#161f33;
  --card:rgba(255,255,255,.045);
  --card-hover:rgba(255,255,255,.075);
  --border:rgba(255,255,255,.09);
  --border-strong:rgba(255,255,255,.16);
  --text:#e8ecf5;
  --muted:#94a3b8;
  --primary:#6366f1;
  --primary-2:#8b5cf6;
  --accent:#22d3ee;
  --success:#10b981;
  --danger:#ef4444;
  --warning:#f59e0b;
  --radius:16px;
  --radius-sm:10px;
  --shadow:0 20px 50px -12px rgba(0,0,0,.6);
  --nav-bg:rgba(11,15,25,.72);
}
[data-theme="light"]{
  --bg:#f6f7fb;
  --bg-2:#ffffff;
  --bg-3:#eef1f8;
  --card:rgba(15,23,42,.03);
  --card-hover:rgba(15,23,42,.06);
  --border:rgba(15,23,42,.09);
  --border-strong:rgba(15,23,42,.18);
  --text:#0f172a;
  --muted:#64748b;
  --shadow:0 20px 50px -12px rgba(15,23,42,.18);
  --nav-bg:rgba(246,247,251,.78);
}

/* ============ BASE ============ */
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
  font-family:'Inter',system-ui,-apple-system,'Segoe UI',Roboto,sans-serif;
  background:var(--bg);
  color:var(--text);
  line-height:1.65;
  -webkit-font-smoothing:antialiased;
  overflow-x:hidden;
  transition:background .3s,color .3s;
}
a{color:inherit;text-decoration:none}
button,input,select,textarea{font-family:inherit;font-size:inherit;color:inherit}
img{max-width:100%;display:block}
::selection{background:var(--primary);color:#fff}

/* scrollbar */
::-webkit-scrollbar{width:10px;height:10px}
::-webkit-scrollbar-track{background:transparent}
::-webkit-scrollbar-thumb{background:var(--border-strong);border-radius:99px;border:2px solid transparent;background-clip:content-box}
::-webkit-scrollbar-thumb:hover{background:var(--muted);background-clip:content-box}

/* ============ BACKGROUND GLOW ============ */
.bg-glow{position:fixed;inset:0;pointer-events:none;z-index:0;overflow:hidden}
.bg-glow::before,.bg-glow::after{
  content:'';position:absolute;border-radius:50%;filter:blur(120px);opacity:.35;
}
.bg-glow::before{
  width:600px;height:600px;top:-220px;left:-160px;
  background:radial-gradient(circle,var(--primary),transparent 70%);
}
.bg-glow::after{
  width:560px;height:560px;top:120px;right:-200px;
  background:radial-gradient(circle,var(--accent),transparent 70%);
  opacity:.22;
}
[data-theme="light"] .bg-glow::before{opacity:.18}
[data-theme="light"] .bg-glow::after{opacity:.13}

/* ============ LAYOUT ============ */
.wrap{max-width:1200px;margin:0 auto;padding:0 22px;position:relative;z-index:1}

/* ============ NAV ============ */
.nav{
  position:sticky;top:0;z-index:60;
  backdrop-filter:blur(18px) saturate(180%);
  -webkit-backdrop-filter:blur(18px) saturate(180%);
  background:var(--nav-bg);
  border-bottom:1px solid var(--border);
}
.nav-inner{
  max-width:1200px;margin:0 auto;padding:14px 22px;
  display:flex;align-items:center;gap:28px;
}
.logo{display:flex;align-items:center;gap:10px;font-weight:800;font-size:1.12rem;letter-spacing:-.02em;flex-shrink:0}
.logo-mark{
  width:34px;height:34px;border-radius:10px;display:grid;place-items:center;
  background:linear-gradient(135deg,var(--primary),var(--primary-2));
  color:#fff;font-size:1rem;font-weight:800;
  box-shadow:0 6px 18px -6px var(--primary);
}
.logo span{background:linear-gradient(135deg,var(--text),var(--muted));-webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.nav-links{display:flex;gap:26px;margin-left:auto;font-size:.9rem;font-weight:500}
.nav-links a{color:var(--muted);transition:color .2s;position:relative}
.nav-links a:hover{color:var(--text)}
.nav-links a::after{
  content:'';position:absolute;left:0;bottom:-6px;height:2px;width:0;
  background:linear-gradient(90deg,var(--primary),var(--accent));
  transition:width .25s;border-radius:2px;
}
.nav-links a:hover::after{width:100%}
.nav-actions{display:flex;align-items:center;gap:10px}
.icon-btn{
  width:38px;height:38px;border-radius:10px;border:1px solid var(--border);
  background:var(--card);display:grid;place-items:center;cursor:pointer;
  transition:.2s;font-size:1rem;
}
.icon-btn:hover{background:var(--card-hover);border-color:var(--border-strong);transform:translateY(-1px)}
@media(max-width:860px){.nav-links{display:none}}

/* ============ HERO ============ */
.hero{padding:82px 0 54px;text-align:center;position:relative;z-index:1}
.pill{
  display:inline-flex;align-items:center;gap:8px;
  padding:7px 16px;border-radius:99px;font-size:.78rem;font-weight:600;
  border:1px solid var(--border);background:var(--card);
  color:var(--muted);margin-bottom:26px;letter-spacing:.02em;
  backdrop-filter:blur(8px);
}
.pill .dot{width:7px;height:7px;border-radius:50%;background:var(--success);box-shadow:0 0 10px var(--success);animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.35}}
.hero h1{
  font-size:clamp(2.1rem,6vw,4rem);line-height:1.08;font-weight:800;
  letter-spacing:-.035em;margin-bottom:20px;
}
.hero h1 .grad{
  background:linear-gradient(120deg,var(--primary) 0%,var(--primary-2) 40%,var(--accent) 100%);
  -webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent;
}
.hero p.lead{
  font-size:clamp(1rem,2vw,1.15rem);color:var(--muted);
  max-width:640px;margin:0 auto 36px;
}
.hero-actions{display:flex;gap:12px;justify-content:center;flex-wrap:wrap;margin-bottom:44px}
.btn{
  display:inline-flex;align-items:center;gap:9px;
  padding:13px 26px;border-radius:12px;font-weight:600;font-size:.93rem;
  border:1px solid transparent;cursor:pointer;transition:.22s;white-space:nowrap;
}
.btn-primary{
  background:linear-gradient(135deg,var(--primary),var(--primary-2));
  color:#fff;box-shadow:0 10px 30px -10px var(--primary);
}
.btn-primary:hover{transform:translateY(-2px);box-shadow:0 16px 36px -10px var(--primary)}
.btn-ghost{background:var(--card);border-color:var(--border);color:var(--text)}
.btn-ghost:hover{background:var(--card-hover);border-color:var(--border-strong);transform:translateY(-2px)}

/* search */
.search-box{
  max-width:520px;margin:0 auto 12px;position:relative;
}
.search-box input{
  width:100%;padding:15px 20px 15px 48px;border-radius:14px;
  border:1px solid var(--border);background:var(--card);
  outline:none;transition:.22s;font-size:.95rem;
  backdrop-filter:blur(10px);
}
.search-box input:focus{border-color:var(--primary);background:var(--card-hover);box-shadow:0 0 0 4px rgba(99,102,241,.12)}
.search-box .ico{position:absolute;left:18px;top:50%;transform:translateY(-50%);color:var(--muted);font-size:1rem;pointer-events:none}

/* stats */
.stats{display:flex;justify-content:center;gap:44px;flex-wrap:wrap;margin-top:44px}
.stat{text-align:center}
.stat b{display:block;font-size:1.55rem;font-weight:800;letter-spacing:-.02em;
  background:linear-gradient(135deg,var(--primary),var(--accent));
  -webkit-background-clip:text;background-clip:text;-webkit-text-fill-color:transparent}
.stat span{font-size:.78rem;color:var(--muted);text-transform:uppercase;letter-spacing:.09em;font-weight:600}

/* ============ SECTIONS ============ */
section{padding:56px 0;position:relative;z-index:1}
.section-head{text-align:center;margin-bottom:42px}
.section-head h2{font-size:clamp(1.6rem,4vw,2.3rem);font-weight:800;letter-spacing:-.03em;margin-bottom:12px}
.section-head p{color:var(--muted);max-width:560px;margin:0 auto;font-size:.97rem}

/* ============ TOOL GRID ============ */
.tools-grid{
  display:grid;grid-template-columns:repeat(auto-fill,minmax(268px,1fr));gap:18px;
}
.tool-card{
  position:relative;padding:26px 24px 24px;border-radius:var(--radius);
  border:1px solid var(--border);background:var(--card);
  cursor:pointer;transition:.28s cubic-bezier(.2,.8,.3,1);
  overflow:hidden;backdrop-filter:blur(10px);
}
.tool-card::before{
  content:'';position:absolute;inset:0;opacity:0;transition:opacity .3s;
  background:radial-gradient(400px circle at var(--mx,50%) var(--my,0%),rgba(99,102,241,.13),transparent 65%);
  pointer-events:none;
}
.tool-card:hover::before{opacity:1}
.tool-card:hover{transform:translateY(-5px);border-color:var(--border-strong);background:var(--card-hover);box-shadow:var(--shadow)}
.tool-icon{
  width:50px;height:50px;border-radius:14px;display:grid;place-items:center;
  font-size:1.4rem;margin-bottom:18px;
  background:linear-gradient(135deg,var(--i1,#6366f1),var(--i2,#8b5cf6));
  box-shadow:0 10px 24px -10px var(--i1,#6366f1);
  transition:transform .28s;
}
.tool-card:hover .tool-icon{transform:scale(1.07) rotate(-4deg)}
.tool-card h3{font-size:1.03rem;font-weight:700;margin-bottom:7px;letter-spacing:-.01em}
.tool-card p{font-size:.855rem;color:var(--muted);line-height:1.55;margin-bottom:16px}
.tool-tag{
  display:inline-block;font-size:.68rem;font-weight:700;letter-spacing:.07em;
  text-transform:uppercase;padding:4px 10px;border-radius:6px;
  background:rgba(99,102,241,.14);color:#a5b4fc;border:1px solid rgba(99,102,241,.22);
}
[data-theme="light"] .tool-tag{color:var(--primary)}
.tool-card.hide{display:none}
.no-results{grid-column:1/-1;text-align:center;padding:56px 20px;color:var(--muted);font-size:.95rem}

/* ============ FEATURES ============ */
.features-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:18px}
.feature{
  padding:26px;border-radius:var(--radius);border:1px solid var(--border);
  background:var(--card);transition:.25s;
}
.feature:hover{border-color:var(--border-strong);transform:translateY(-3px)}
.feature .fi{
  width:42px;height:42px;border-radius:12px;display:grid;place-items:center;
  font-size:1.15rem;margin-bottom:16px;background:var(--bg-3);border:1px solid var(--border);
}
.feature h4{font-size:.98rem;font-weight:700;margin-bottom:7px}
.feature p{font-size:.855rem;color:var(--muted);line-height:1.6}

/* ============ CTA ============ */
.cta-box{
  border-radius:24px;padding:54px 34px;text-align:center;
  border:1px solid var(--border);position:relative;overflow:hidden;
  background:linear-gradient(135deg,rgba(99,102,241,.13),rgba(34,211,238,.07));
}
.cta-box h2{font-size:clamp(1.5rem,4vw,2.1rem);font-weight:800;letter-spacing:-.03em;margin-bottom:14px}
.cta-box p{color:var(--muted);max-width:520px;margin:0 auto 28px;font-size:.95rem}

/* ============ FOOTER ============ */
footer{border-top:1px solid var(--border);padding:44px 0 30px;margin-top:40px;position:relative;z-index:1}
.foot-grid{display:flex;justify-content:space-between;gap:30px;flex-wrap:wrap;margin-bottom:34px}
.foot-brand{max-width:300px}
.foot-brand p{font-size:.85rem;color:var(--muted);margin-top:12px;line-height:1.6}
.foot-col h5{font-size:.78rem;text-transform:uppercase;letter-spacing:.1em;color:var(--muted);margin-bottom:14px;font-weight:700}
.foot-col a{display:block;font-size:.87rem;color:var(--muted);margin-bottom:9px;transition:color .2s}
.foot-col a:hover{color:var(--text)}
.foot-bottom{
  border-top:1px solid var(--border);padding-top:22px;
  display:flex;justify-content:space-between;gap:16px;flex-wrap:wrap;
  font-size:.8rem;color:var(--muted);
}

/* ============ MODAL ============ */
.modal-overlay{
  position:fixed;inset:0;z-index:200;display:none;
  align-items:center;justify-content:center;padding:18px;
  background:rgba(3,6,15,.72);backdrop-filter:blur(8px);
}
.modal-overlay.open{display:flex;animation:fade .2s ease}
@keyframes fade{from{opacity:0}to{opacity:1}}
.modal{
  background:var(--bg-2);border:1px solid var(--border);
  border-radius:20px;width:100%;max-width:540px;max-height:92vh;
  display:flex;flex-direction:column;overflow:hidden;
  box-shadow:0 40px 90px -20px rgba(0,0,0,.7);
  animation:pop .28s cubic-bezier(.2,.9,.3,1.1);
}
.modal.wide{max-width:720px}
@keyframes pop{from{opacity:0;transform:translateY(18px) scale(.97)}to{opacity:1;transform:none}}
.modal-head{
  display:flex;align-items:center;gap:12px;padding:18px 20px;
  border-bottom:1px solid var(--border);flex-shrink:0;
}
.modal-head .mi{
  width:36px;height:36px;border-radius:10px;display:grid;place-items:center;
  font-size:1.05rem;background:linear-gradient(135deg,var(--i1,#6366f1),var(--i2,#8b5cf6));
}
.modal-head h3{font-size:1rem;font-weight:700;flex:1;letter-spacing:-.01em}
.modal-close{
  width:34px;height:34px;border-radius:9px;border:1px solid var(--border);
  background:transparent;cursor:pointer;color:var(--muted);
  display:grid;place-items:center;font-size:1rem;transition:.2s;
}
.modal-close:hover{background:var(--card-hover);color:var(--text);border-color:var(--border-strong)}
.modal-body{padding:22px;overflow-y:auto;flex:1}

/* ============ FORM CONTROLS ============ */
.field{margin-bottom:16px}
.field label{display:block;font-size:.79rem;font-weight:600;color:var(--muted);margin-bottom:7px;letter-spacing:.02em}
.input,textarea.input,select.input{
  width:100%;padding:11px 14px;border-radius:var(--radius-sm);
  border:1px solid var(--border);background:var(--bg-3);
  outline:none;transition:.2s;font-size:.9rem;
}
.input:focus{border-color:var(--primary);box-shadow:0 0 0 3px rgba(99,102,241,.13)}
textarea.input{resize:vertical;min-height:100px;line-height:1.6}
select.input{cursor:pointer;appearance:none;
  background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='12' height='12' viewBox='0 0 12 12'%3E%3Cpath fill='%2394a3b8' d='M6 8L2 4h8z'/%3E%3C/svg%3E");
  background-repeat:no-repeat;background-position:right 14px center;padding-right:38px;
}
input[type=range]{
  -webkit-appearance:none;appearance:none;width:100%;height:6px;
  border-radius:99px;background:var(--bg-3);outline:none;cursor:pointer;border:1px solid var(--border);
}
input[type=range]::-webkit-slider-thumb{
  -webkit-appearance:none;width:18px;height:18px;border-radius:50%;
  background:linear-gradient(135deg,var(--primary),var(--primary-2));cursor:pointer;
  box-shadow:0 2px 10px -2px var(--primary);
}
input[type=range]::-moz-range-thumb{
  width:18px;height:18px;border:none;border-radius:50%;
  background:linear-gradient(135deg,var(--primary),var(--primary-2));cursor:pointer;
}
.row{display:flex;gap:12px}
.row>*{flex:1;min-width:0}
.btn-sm{
  padding:10px 18px;border-radius:var(--radius-sm);font-weight:600;font-size:.86rem;
  border:1px solid transparent;cursor:pointer;transition:.2s;
}
.btn-full{width:100%;justify-content:center}
.btn-primary.btn-sm{background:linear-gradient(135deg,var(--primary),var(--primary-2));color:#fff}
.btn-primary.btn-sm:hover{transform:translateY(-1px);box-shadow:0 10px 24px -10px var(--primary)}
.btn-ghost.btn-sm{background:var(--card);border-color:var(--border);color:var(--text)}
.btn-ghost.btn-sm:hover{background:var(--card-hover);border-color:var(--border-strong)}
.btn:disabled,.btn-sm:disabled{opacity:.5;cursor:not-allowed;transform:none!important;box-shadow:none!important}

/* ============ CALCULATOR ============ */
.calc-display{
  background:var(--bg-3);border:1px solid var(--border);border-radius:14px;
  padding:20px 18px;margin-bottom:16px;text-align:right;overflow:hidden;
}
.calc-expr{font-size:.82rem;color:var(--muted);min-height:20px;word-break:break-all;font-variant-numeric:tabular-nums}
.calc-current{
  font-size:2.4rem;font-weight:700;letter-spacing:-.03em;word-break:break-all;
  font-variant-numeric:tabular-nums;line-height:1.2;margin-top:4px;
}
.calc-pad{display:grid;grid-template-columns:repeat(4,1fr);gap:9px}
.cbtn{
  padding:16px 6px;border-radius:13px;border:1px solid var(--border);
  background:var(--card);cursor:pointer;font-size:1.05rem;font-weight:600;
  transition:.15s;user-select:none;
}
.cbtn:hover{background:var(--card-hover);border-color:var(--border-strong)}
.cbtn:active{transform:scale(.95)}
.cbtn.fn{color:var(--muted);font-size:.95rem}
.cbtn.op{color:var(--accent);background:rgba(34,211,238,.08);border-color:rgba(34,211,238,.18)}
.cbtn.op:hover{background:rgba(34,211,238,.15)}
.cbtn.eq{
  background:linear-gradient(135deg,var(--primary),var(--primary-2));
  color:#fff;border-color:transparent;box-shadow:0 8px 22px -10px var(--primary);
}
.cbtn.eq:hover{filter:brightness(1.1)}
.calc-hint{font-size:.75rem;color:var(--muted);text-align:center;margin-top:14px}

/* ============ DROPZONE ============ */
.dropzone{
  border:2px dashed var(--border-strong);border-radius:14px;
  padding:34px 20px;text-align:center;cursor:pointer;transition:.25s;
  background:var(--card);
}
.dropzone:hover,.dropzone.drag{border-color:var(--primary);background:rgba(99,102,241,.07)}
.dropzone .dz-ico{font-size:1.9rem;margin-bottom:10px;opacity:.85}
.dropzone p{font-size:.87rem;color:var(--muted)}
.dropzone b{color:var(--text);font-weight:600}

/* ============ RESULT BOX ============ */
.result{
  margin-top:16px;padding:16px;border-radius:12px;
  background:var(--bg-3);border:1px solid var(--border);font-size:.86rem;
}
.result-grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:14px}
.result-grid .k{font-size:.72rem;text-transform:uppercase;letter-spacing:.08em;color:var(--muted);font-weight:700;margin-bottom:3px}
.result-grid .v{font-size:1rem;font-weight:700;font-variant-numeric:tabular-nums}
.v.good{color:var(--success)}
.v.bad{color:var(--warning)}
.preview-img{
  width:100%;border-radius:10px;border:1px solid var(--border);
  max-height:200px;object-fit:contain;background:var(--bg-2);margin-bottom:14px;
}
.note{
  font-size:.79rem;color:var(--muted);padding:11px 14px;border-radius:10px;
  background:rgba(99,102,241,.07);border:1px solid rgba(99,102,241,.16);
  line-height:1.55;margin-top:14px;
}
.note.warn{background:rgba(245,158,11,.08);border-color:rgba(245,158,11,.2);color:#fcd34d}
[data-theme="light"] .note.warn{color:#92400e}

/* ============ AI ============ */
.ai-output{
  min-height:130px;padding:16px;border-radius:12px;background:var(--bg-3);
  border:1px solid var(--border);font-size:.88rem;line-height:1.7;
  white-space:pre-wrap;word-wrap:break-word;overflow-y:auto;max-height:300px;
}
.ai-output.placeholder{color:var(--muted);font-style:italic}
.settings-panel{
  border:1px solid var(--border);border-radius:12px;padding:16px;
  background:var(--card);margin-bottom:16px;
}
.settings-panel summary{
  cursor:pointer;font-size:.83rem;font-weight:600;color:var(--muted);
  list-style:none;display:flex;align-items:center;gap:8px;
}
.settings-panel summary::-webkit-details-marker{display:none}
.settings-panel summary::before{content:'⚙';font-size:.95rem}
.settings-panel[open] summary{margin-bottom:14px;color:var(--text)}
.spinner{
  display:inline-block;width:15px;height:15px;border-radius:50%;
  border:2px solid rgba(255,255,255,.3);border-top-color:#fff;
  animation:spin .7s linear infinite;vertical-align:-2px;margin-right:7px;
}
@keyframes spin{to{transform:rotate(360deg)}}

/* ============ MISC TOOL UI ============ */
.chip-row{display:flex;gap:8px;flex-wrap:wrap;margin-bottom:14px}
.chip{
  padding:7px 14px;border-radius:99px;border:1px solid var(--border);
  background:var(--card);font-size:.8rem;font-weight:600;cursor:pointer;transition:.2s;
}
.chip:hover{border-color:var(--border-strong);background:var(--card-hover)}
.chip.active{background:linear-gradient(135deg,var(--primary),var(--primary-2));color:#fff;border-color:transparent}
.pw-output{
  font-family:ui-monospace,'SF Mono',Menlo,monospace;font-size:1.15rem;font-weight:600;
  padding:16px;border-radius:12px;background:var(--bg-3);border:1px solid var(--border);
  word-break:break-all;text-align:center;letter-spacing:.02em;margin-bottom:14px;min-height:56px;
  display:flex;align-items:center;justify-content:center;
}
.meter{height:6px;border-radius:99px;background:var(--bg-3);overflow:hidden;margin-bottom:16px;border:1px solid var(--border)}
.meter i{display:block;height:100%;width:0;transition:width .3s,background .3s;border-radius:99px}
.stat-row{display:grid;grid-template-columns:repeat(auto-fit,minmax(90px,1fr));gap:10px;margin-bottom:16px}
.stat-mini{padding:12px;border-radius:10px;background:var(--bg-3);border:1px solid var(--border);text-align:center}
.stat-mini b{display:block;font-size:1.2rem;font-weight:800;font-variant-numeric:tabular-nums}
.stat-mini span{font-size:.68rem;color:var(--muted);text-transform:uppercase;letter-spacing:.07em;font-weight:700}

/* ============ TOAST ============ */
#toasts{position:fixed;bottom:24px;right:24px;z-index:500;display:flex;flex-direction:column;gap:10px;pointer-events:none}
.toast{
  padding:13px 20px;border-radius:12px;font-size:.86rem;font-weight:600;
  background:var(--bg-2);border:1px solid var(--border-strong);
  box-shadow:0 16px 40px -12px rgba(0,0,0,.6);
  opacity:0;transform:translateX(24px);transition:.3s cubic-bezier(.2,.9,.3,1);
  max-width:320px;
}
.toast.show{opacity:1;transform:none}
.toast.success{border-color:rgba(16,185,129,.4)}
.toast.error{border-color:rgba(239,68,68,.4)}
@media(max-width:520px){
  #toasts{left:16px;right:16px;bottom:16px}
  .toast{max-width:none}
  .hero{padding:56px 0 40px}
  .stats{gap:28px}
  .modal-body{padding:18px}
}
</style>
</head>
<body>

<div class="bg-glow"></div>

<!-- ================= NAV ================= -->
<header class="nav">
  <div class="nav-inner">
    <a href="#" class="logo">
      <span class="logo-mark">N</span>
      <span>NexusTools</span>
    </a>
    <nav class="nav-links">
      <a href="#tools">Tools</a>
      <a href="#features">Features</a>
      <a href="#about">About</a>
    </nav>
    <div class="nav-actions">
      <button class="icon-btn" id="themeToggle" title="Toggle theme" aria-label="Toggle theme">🌙</button>
    </div>
  </div>
</header>

<main>

<!-- ================= HERO ================= -->
<section class="hero">
  <div class="wrap">
    <div class="pill"><span class="dot"></span> 100% Free · No Signup · Runs in Your Browser</div>
    <h1>Every Tool You Need.<br><span class="grad">One Powerful Workspace.</span></h1>
    <p class="lead">
      Compress images, shrink PDFs, run calculations, generate QR codes, create strong passwords,
      and tap into AI assistance — all in one fast, private, professional suite.
    </p>
    <div class="hero-actions">
      <a href="#tools" class="btn btn-primary">Explore All Tools →</a>
      <button class="btn btn-ghost" data-tool="ai">✨ Try the AI Assistant</button>
    </div>

    <div class="search-box">
      <span class="ico">🔍</span>
      <input type="text" id="toolSearch" placeholder="Search tools… (calculator, compress, qr, password)" autocomplete="off">
    </div>

    <div class="stats">
      <div class="stat"><b>8+</b><span>Pro Tools</span></div>
      <div class="stat"><b>0 KB</b><span>Uploaded to Servers</span></div>
      <div class="stat"><b>100%</b><span>Free Forever</span></div>
      <div class="stat"><b>&lt;1s</b><span>Processing</span></div>
    </div>
  </div>
</section>

<!-- ================= TOOLS ================= -->
<section id="tools">
  <div class="wrap">
    <div class="section-head">
      <h2>All Tools</h2>
      <p>Click any tool to open it instantly. Files are processed locally on your device — nothing is ever uploaded.</p>
    </div>

    <div class="tools-grid" id="toolsGrid">

      <article class="tool-card" data-tool="calc" data-tags="calculator math numbers arithmetic percent">
        <div class="tool-icon" style="--i1:#6366f1;--i2:#8b5cf6">🧮</div>
        <h3>Advanced Calculator</h3>
        <p>Fast, keyboard-friendly calculator with percentages, sign toggle and full expression history.</p>
        <span class="tool-tag">Essential</span>
      </article>

      <article class="tool-card" data-tool="image" data-tags="image compressor jpg png webp photo optimize reduce">
        <div class="tool-icon" style="--i1:#22d3ee;--i2:#0ea5e9">🖼️</div>
        <h3>Image Compressor</h3>
        <p>Shrink JPG, PNG and WebP files by up to 90% with quality and resize controls — right in your browser.</p>
        <span class="tool-tag">Popular</span>
      </article>

      <article class="tool-card" data-tool="pdf" data-tags="pdf compressor optimize reduce shrink document">
        <div class="tool-icon" style="--i1:#f43f5e;--i2:#e11d48">📄</div>
        <h3>PDF Compressor</h3>
        <p>Optimize and rebuild PDF documents to strip redundant data and reduce file size safely.</p>
        <span class="tool-tag">Popular</span>
      </article>

      <article class="tool-card" data-tool="ai" data-tags="ai assistant summarize rewrite explain gpt chat">
        <div class="tool-icon" style="--i1:#a855f7;--i2:#6366f1">✨</div>
        <h3>AI Assistant</h3>
        <p>Summarize, rewrite, explain or generate content with a built-in AI workspace. Bring your own API key.</p>
        <span class="tool-tag">Advanced</span>
      </article>

      <article class="tool-card" data-tool="qr" data-tags="qr code generator barcode link url share">
        <div class="tool-icon" style="--i1:#10b981;--i2:#059669">🔳</div>
        <h3>QR Code Generator</h3>
        <p>Create high-resolution QR codes for links, text or contact info. Download as PNG instantly.</p>
        <span class="tool-tag">Utility</span>
      </article>

      <article class="tool-card" data-tool="password" data-tags="password generator secure random strong key">
        <div class="tool-icon" style="--i1:#f59e0b;--i2:#ea580c">🔐</div>
        <h3>Password Generator</h3>
        <p>Generate cryptographically strong passwords with a live strength meter and one-click copy.</p>
        <span class="tool-tag">Security</span>
      </article>

      <article class="tool-card" data-tool="convert" data-tags="unit converter length weight data temperature metric">
        <div class="tool-icon" style="--i1:#8b5cf6;--i2:#d946ef">📐</div>
        <h3>Unit Converter</h3>
        <p>Convert length, weight, data sizes and temperature between metric and imperial units.</p>
        <span class="tool-tag">Utility</span>
      </article>

      <article class="tool-card" data-tool="text" data-tags="text tools word count case converter uppercase lowercase">
        <div class="tool-icon" style="--i1:#0ea5e9;--i2:#6366f1">📝</div>
        <h3>Text Tools</h3>
        <p>Live word & character counts, reading time, case conversion, cleanup and instant copy.</p>
        <span class="tool-tag">Writing</span>
      </article>

    </div>
  </div>
</section>

<!-- ================= FEATURES ================= -->
<section id="features">
  <div class="wrap">
    <div class="section-head">
      <h2>Built for Speed & Privacy</h2>
      <p>Everything runs on your own device. No uploads, no queues, no accounts.</p>
    </div>
    <div class="features-grid">
      <div class="feature">
        <div class="fi">🔒</div>
        <h4>Private by Design</h4>
        <p>Image and PDF processing happens entirely in your browser using client-side APIs. Your files never touch a server.</p>
      </div>
      <div class="feature">
        <div class="fi">⚡</div>
        <h4>Instant Results</h4>
        <p>No upload or download round-trips. Compression and conversions complete in milliseconds.</p>
      </div>
      <div class="feature">
        <div class="fi">📱</div>
        <h4>Works Everywhere</h4>
        <p>Fully responsive interface designed for desktop, tablet and mobile browsers alike.</p>
      </div>
      <div class="feature">
        <div class="fi">🎯</div>
        <h4>No Limits, No Cost</h4>
        <p>Unlimited usage with no watermarks, file caps, sign-ups or hidden premium tiers.</p>
      </div>
    </div>
  </div>
</section>

<!-- ================= CTA ================= -->
<section id="about">
  <div class="wrap">
    <div class="cta-box">
      <h2>Your All-in-One Digital Toolbox</h2>
      <p>Bookmark NexusTools and replace a dozen clunky websites with one clean, fast and private workspace.</p>
      <button class="btn btn-primary" data-tool="image">🚀 Start with Image Compressor</button>
    </div>
  </div>
</section>

</main>

<!-- ================= FOOTER ================= -->
<footer>
  <div class="wrap">
    <div class="foot-grid">
      <div class="foot-brand">
        <a href="#" class="logo">
          <span class="logo-mark">N</span>
          <span>NexusTools</span>
        </a>
        <p>A professional suite of free browser-based utilities for creators, developers and everyday users.</p>
      </div>
      <div class="foot-col">
        <h5>Tools</h5>
        <a href="#" data-tool="calc">Calculator</a>
        <a href="#" data-tool="image">Image Compressor</a>
        <a href="#" data-tool="pdf">PDF Compressor</a>
        <a href="#" data-tool="ai">AI Assistant</a>
      </div>
      <div class="foot-col">
        <h5>More</h5>
        <a href="#" data-tool="qr">QR Generator</a>
        <a href="#" data-tool="password">Password Generator</a>
        <a href="#" data-tool="convert">Unit Converter</a>
        <a href="#" data-tool="text">Text Tools</a>
      </div>
      <div class="foot-col">
        <h5>Company</h5>
        <a href="#features">Features</a>
        <a href="#about">About</a>
        <a href="#">Privacy</a>
        <a href="#">Contact</a>
      </div>
    </div>
    <div class="foot-bottom">
      <span>© <span id="year"></span> NexusTools. All rights reserved.</span>
      <span>Built with ❤️ — runs entirely in your browser.</span>
    </div>
  </div>
</footer>

<!-- ============================================================
     MODALS
============================================================ -->

<!-- CALCULATOR -->
<div class="modal-overlay" id="modal-calc">
  <div class="modal">
    <div class="modal-head">
      <div class="mi" style="--i1:#6366f1;--i2:#8b5cf6">🧮</div>
      <h3>Advanced Calculator</h3>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body">
      <div class="calc-display">
        <div class="calc-expr" id="calcExpr"></div>
        <div class="calc-current" id="calcCurrent">0</div>
      </div>
      <div class="calc-pad" id="calcPad">
        <button class="cbtn fn" data-fn="ac">AC</button>
        <button class="cbtn fn" data-fn="back">⌫</button>
        <button class="cbtn fn" data-fn="pct">%</button>
        <button class="cbtn op" data-op="÷">÷</button>

        <button class="cbtn" data-num="7">7</button>
        <button class="cbtn" data-num="8">8</button>
        <button class="cbtn" data-num="9">9</button>
        <button class="cbtn op" data-op="×">×</button>

        <button class="cbtn" data-num="4">4</button>
        <button class="cbtn" data-num="5">5</button>
        <button class="cbtn" data-num="6">6</button>
        <button class="cbtn op" data-op="−">−</button>

        <button class="cbtn" data-num="1">1</button>
        <button class="cbtn" data-num="2">2</button>
        <button class="cbtn" data-num="3">3</button>
        <button class="cbtn op" data-op="+">+</button>

        <button class="cbtn fn" data-fn="sign">±</button>
        <button class="cbtn" data-num="0">0</button>
        <button class="cbtn" data-num=".">.</button>
        <button class="cbtn eq" data-fn="eq">=</button>
      </div>
      <p class="calc-hint">💡 Tip: use your keyboard — numbers, <b>+ − * /</b>, <b>Enter</b> to equals, <b>Esc</b> to clear.</p>
    </div>
  </div>
</div>

<!-- IMAGE COMPRESSOR -->
<div class="modal-overlay" id="modal-image">
  <div class="modal">
    <div class="modal-head">
      <div class="mi" style="--i1:#22d3ee;--i2:#0ea5e9">🖼️</div>
      <h3>Image Compressor</h3>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body">
      <div class="dropzone" id="imgDrop">
        <div class="dz-ico">📁</div>
        <p><b>Click to choose</b> or drag &amp; drop an image</p>
        <p style="font-size:.78rem;margin-top:6px">JPG · PNG · WebP</p>
      </div>
      <input type="file" id="imgInput" accept="image/*" hidden>

      <div id="imgPanel" style="display:none;margin-top:18px">
        <img id="imgPreview" class="preview-img" alt="Preview">

        <div class="field">
          <label>Output format</label>
          <select class="input" id="imgFormat">
            <option value="image/jpeg">JPEG (smallest)</option>
            <option value="image/webp">WebP (best quality/size)</option>
          </select>
        </div>

        <div class="field">
          <label>Quality — <span id="imgQualityVal">75</span>%</label>
          <input type="range" id="imgQuality" min="10" max="100" value="75" step="5">
        </div>

        <div class="field">
          <label>Max width — <span id="imgWidthVal">1920</span>px</label>
          <input type="range" id="imgWidth" min="320" max="4000" value="1920" step="80">
        </div>

        <button class="btn btn-primary btn-sm btn-full" id="imgRun">⚡ Compress Image</button>

        <div class="result" id="imgResult" style="display:none">
          <div class="result-grid">
            <div><div class="k">Original</div><div class="v" id="imgOrigSize">—</div></div>
            <div><div class="k">Compressed</div><div class="v good" id="imgNewSize">—</div></div>
          </div>
          <div id="imgSaveLine" style="font-size:.84rem;margin-bottom:14px"></div>
          <button class="btn btn-primary btn-sm btn-full" id="imgDownload">⬇ Download Compressed Image</button>
        </div>
      </div>

      <div class="note">🔒 Your image is processed locally with the Canvas API. Nothing is uploaded to any server.</div>
    </div>
  </div>
</div>

<!-- PDF COMPRESSOR -->
<div class="modal-overlay" id="modal-pdf">
  <div class="modal">
    <div class="modal-head">
      <div class="mi" style="--i1:#f43f5e;--i2:#e11d48">📄</div>
      <h3>PDF Compressor</h3>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body">
      <div class="dropzone" id="pdfDrop">
        <div class="dz-ico">📄</div>
        <p><b>Click to choose</b> or drag &amp; drop a PDF</p>
        <p style="font-size:.78rem;margin-top:6px">Optimizes structure &amp; removes metadata</p>
      </div>
      <input type="file" id="pdfInput" accept="application/pdf" hidden>

      <div id="pdfPanel" style="display:none;margin-top:18px">
        <div class="result" style="margin-top:0">
          <div class="result-grid">
            <div><div class="k">Original</div><div class="v" id="pdfOrigSize">—</div></div>
            <div><div class="k">Optimized</div><div class="v" id="pdfNewSize">—</div></div>
          </div>
          <div id="pdfSaveLine" style="font-size:.84rem;margin-bottom:14px"></div>
          <button class="btn btn-primary btn-sm btn-full" id="pdfDownload">⬇ Download Optimized PDF</button>
        </div>
      </div>

      <div class="note">🔒 The PDF is parsed and rebuilt entirely in your browser using pdf-lib. No upload occurs.</div>
      <div class="note warn" id="pdfWarn" style="display:none">
        PDF optimization works best on documents with redundant objects or embedded metadata. Files that are
        already well-optimized may not shrink — in that case we'll keep the original for you.
      </div>
    </div>
  </div>
</div>

<!-- AI ASSISTANT -->
<div class="modal-overlay" id="modal-ai">
  <div class="modal wide">
    <div class="modal-head">
      <div class="mi" style="--i1:#a855f7;--i2:#6366f1">✨</div>
      <h3>AI Assistant</h3>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body">

      <details class="settings-panel">
        <summary>API Settings (bring your own key)</summary>
        <div class="field">
          <label>API Key</label>
          <input type="password" class="input" id="aiKey" placeholder="sk-...">
        </div>
        <div class="field">
          <label>Base URL (OpenAI-compatible)</label>
          <input type="text" class="input" id="aiBase" value="https://api.openai.com/v1">
        </div>
        <div class="field">
          <label>Model</label>
          <input type="text" class="input" id="aiModel" value="gpt-4o-mini">
        </div>
        <button class="btn btn-ghost btn-sm btn-full" id="aiSave">💾 Save Settings</button>
        <div class="note" style="margin-top:12px">
          Settings are stored only in your browser's localStorage. Works with OpenAI, Groq, Together,
          OpenRouter, or any OpenAI-compatible endpoint.
        </div>
      </details>

      <div class="field">
        <label>Task</label>
        <select class="input" id="aiTask">
          <option value="Summarize the following text concisely, capturing all key points:">📌 Summarize</option>
          <option value="Rewrite the following text to be clearer, more professional and more engaging:">✍️ Rewrite / Improve</option>
          <option value="Explain the following in simple, beginner-friendly terms with examples:">💡 Explain Simply</option>
          <option value="Fix all grammar, spelling and punctuation errors in the following text and return the corrected version only:">✅ Fix Grammar</option>
          <option value="Translate the following text into English:">🌐 Translate to English</option>
          <option value="Generate 5 creative ideas, titles or angles related to the following topic:">🚀 Generate Ideas</option>
          <option value="">💬 Custom prompt</option>
        </select>
      </div>

      <div class="field">
        <label>Your input</label>
        <textarea class="input" id="aiInput" placeholder="Paste text or type your prompt here…"></textarea>
      </div>

      <button class="btn btn-primary btn-sm btn-full" id="aiRun">✨ Run AI</button>

      <div class="field" style="margin-top:18px">
        <label>Result</label>
        <div class="ai-output placeholder" id="aiOutput">Your AI response will appear here…</div>
      </div>
    </div>
  </div>
</div>

<!-- QR GENERATOR -->
<div class="modal-overlay" id="modal-qr">
  <div class="modal">
    <div class="modal-head">
      <div class="mi" style="--i1:#10b981;--i2:#059669">🔳</div>
      <h3>QR Code Generator</h3>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body">
      <div class="field">
        <label>Content (URL or text)</label>
        <textarea class="input" id="qrText" placeholder="https://example.com" style="min-height:80px"></textarea>
      </div>
      <div class="row">
        <div class="field">
          <label>Size</label>
          <select class="input" id="qrSize">
            <option value="200">200 × 200</option>
            <option value="300" selected>300 × 300</option>
            <option value="500">500 × 500</option>
            <option value="800">800 × 800</option>
          </select>
        </div>
        <div class="field">
          <label>Margin</label>
          <select class="input" id="qrMargin">
            <option value="0">None</option>
            <option value="1">Small</option>
            <option value="2" selected>Medium</option>
            <option value="4">Large</option>
          </select>
        </div>
      </div>
      <button class="btn btn-primary btn-sm btn-full" id="qrRun">🔳 Generate QR Code</button>

      <div class="result" id="qrResult" style="display:none;text-align:center">
        <img id="qrImg" alt="QR Code" style="margin:0 auto 14px;border-radius:10px;background:#fff;padding:10px;max-width:230px">
        <button class="btn btn-ghost btn-sm btn-full" id="qrDownload">⬇ Download PNG</button>
      </div>
    </div>
  </div>
</div>

<!-- PASSWORD GENERATOR -->
<div class="modal-overlay" id="modal-password">
  <div class="modal">
    <div class="modal-head">
      <div class="mi" style="--i1:#f59e0b;--i2:#ea580c">🔐</div>
      <h3>Password Generator</h3>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body">
      <div class="pw-output" id="pwOutput">Click Generate</div>
      <div class="meter"><i id="pwMeter"></i></div>
      <p style="font-size:.82rem;color:var(--muted);text-align:center;margin-bottom:18px" id="pwLabel">—</p>

      <div class="field">
        <label>Length — <span id="pwLenVal">20</span> characters</label>
        <input type="range" id="pwLen" min="6" max="64" value="20">
      </div>

      <div class="chip-row">
        <button class="chip active" data-pw="upper">A-Z</button>
        <button class="chip active" data-pw="lower">a-z</button>
        <button class="chip active" data-pw="num">0-9</button>
        <button class="chip active" data-pw="sym">!@#$</button>
      </div>

      <div class="row">
        <button class="btn btn-primary btn-sm" id="pwGen" style="flex:1">🔄 Generate</button>
        <button class="btn btn-ghost btn-sm" id="pwCopy" style="flex:1">📋 Copy</button>
      </div>

      <div class="note">🔒 Generated locally with the Web Crypto API — cryptographically secure randomness.</div>
    </div>
  </div>
</div>

<!-- UNIT CONVERTER -->
<div class="modal-overlay" id="modal-convert">
  <div class="modal">
    <div class="modal-head">
      <div class="mi" style="--i1:#8b5cf6;--i2:#d946ef">📐</div>
      <h3>Unit Converter</h3>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body">
      <div class="chip-row" id="convCats">
        <button class="chip active" data-cat="length">Length</button>
        <button class="chip" data-cat="weight">Weight</button>
        <button class="chip" data-cat="data">Data</button>
        <button class="chip" data-cat="temp">Temperature</button>
      </div>

      <div class="field">
        <label>Value</label>
        <input type="number" class="input" id="convValue" value="1" step="any">
      </div>

      <div class="row">
        <div class="field">
          <label>From</label>
          <select class="input" id="convFrom"></select>
        </div>
        <div class="field">
          <label>To</label>
          <select class="input" id="convTo"></select>
        </div>
      </div>

      <div class="result" style="text-align:center">
        <div class="k" style="font-size:.72rem;text-transform:uppercase;letter-spacing:.08em;color:var(--muted);font-weight:700;margin-bottom:6px">Result</div>
        <div id="convResult" style="font-size:1.5rem;font-weight:800;letter-spacing:-.02em;word-break:break-all">1</div>
      </div>
    </div>
  </div>
</div>

<!-- TEXT TOOLS -->
<div class="modal-overlay" id="modal-text">
  <div class="modal wide">
    <div class="modal-head">
      <div class="mi" style="--i1:#0ea5e9;--i2:#6366f1">📝</div>
      <h3>Text Tools</h3>
      <button class="modal-close" data-close>✕</button>
    </div>
    <div class="modal-body">
      <div class="stat-row">
        <div class="stat-mini"><b id="tWords">0</b><span>Words</span></div>
        <div class="stat-mini"><b id="tChars">0</b><span>Chars</span></div>
        <div class="stat-mini"><b id="tSent">0</b><span>Sentences</span></div>
        <div class="stat-mini"><b id="tRead">0m</b><span>Read Time</span></div>
      </div>

      <textarea class="input" id="textArea" placeholder="Start typing or paste your text here…" style="min-height:180px"></textarea>

      <div class="chip-row" style="margin-top:16px">
        <button class="chip" data-tx="upper">UPPERCASE</button>
        <button class="chip" data-tx="lower">lowercase</button>
        <button class="chip" data-tx="title">Title Case</button>
        <button class="chip" data-tx="sentence">Sentence case</button>
        <button class="chip" data-tx="trim">Remove Extra Spaces</button>
        <button class="chip" data-tx="reverse">Reverse</button>
        <button class="chip" data-tx="clear">Clear</button>
        <button class="chip" data-tx="copy">📋 Copy</button>
      </div>
    </div>
  </div>
</div>

<div id="toasts"></div>

<!-- PDF library -->
<script src="https://unpkg.com/pdf-lib@1.17.1/dist/pdf-lib.min.js"></script>

<script>
(function(){
'use strict';

/* ============================================================
   HELPERS
============================================================ */
const $  = (s, c) => (c || document).querySelector(s);
const $$ = (s, c) => Array.from((c || document).querySelectorAll(s));

function formatBytes(bytes){
  if(bytes === 0 || bytes == null) return '0 B';
  const k = 1024, sizes = ['B','KB','MB','GB'];
  const i = Math.floor(Math.log(bytes) / Math.log(k));
  return parseFloat((bytes / Math.pow(k, i)).toFixed(2)) + ' ' + sizes[i];
}

function toast(msg, type){
  const el = document.createElement('div');
  el.className = 'toast' + (type ? ' ' + type : '');
  el.textContent = msg;
  const box = $('#toasts');
  box.appendChild(el);
  requestAnimationFrame(() => el.classList.add('show'));
  setTimeout(() => {
    el.classList.remove('show');
    setTimeout(() => el.remove(), 320);
  }, 2600);
}

async function copyText(text){
  try{
    await navigator.clipboard.writeText(text);
    toast('Copied to clipboard!', 'success');
    return true;
  }catch(e){
    const ta = document.createElement('textarea');
    ta.value = text; ta.style.position = 'fixed'; ta.style.opacity = '0';
    document.body.appendChild(ta); ta.select();
    try{ document.execCommand('copy'); toast('Copied to clipboard!', 'success'); }
    catch(err){ toast('Copy failed', 'error'); }
    ta.remove();
  }
}

/* ============================================================
   THEME
============================================================ */
const themeToggle = $('#themeToggle');
const savedTheme = localStorage.getItem('nexus-theme') || 'dark';
document.documentElement.setAttribute('data-theme', savedTheme);
themeToggle.textContent = savedTheme === 'dark' ? '🌙' : '☀️';

themeToggle.addEventListener('click', () => {
  const next = document.documentElement.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
  document.documentElement.setAttribute('data-theme', next);
  themeToggle.textContent = next === 'dark' ? '🌙' : '☀️';
  localStorage.setItem('nexus-theme', next);
});

$('#year').textContent = new Date().getFullYear();

/* ============================================================
   MODAL SYSTEM
============================================================ */
let openModalEl = null;

function openTool(name){
  const el = document.getElementById('modal-' + name);
  if(!el) return;
  if(openModalEl) openModalEl.classList.remove('open');
  el.classList.add('open');
  openModalEl = el;
  document.body.style.overflow = 'hidden';
  const focusable = el.querySelector('input, textarea, select, button.btn-primary');
  if(focusable) setTimeout(() => focusable.focus(), 120);
}

function closeModal(){
  if(!openModalEl) return;
  openModalEl.classList.remove('open');
  openModalEl = null;
  document.body.style.overflow = '';
}

document.addEventListener('click', (e) => {
  const trigger = e.target.closest('[data-tool]');
  if(trigger){
    e.preventDefault();
    openTool(trigger.getAttribute('data-tool'));
    return;
  }
  if(e.target.closest('[data-close]') || e.target.classList.contains('modal-overlay')){
    closeModal();
  }
});

document.addEventListener('keydown', (e) => {
  if(e.key === 'Escape' && openModalEl) closeModal();
});

/* card pointer glow */
$$('.tool-card').forEach(card => {
  card.addEventListener('mousemove', (e) => {
    const r = card.getBoundingClientRect();
    card.style.setProperty('--mx', (e.clientX - r.left) + 'px');
    card.style.setProperty('--my', (e.clientY - r.top) + 'px');
  });
});

/* ============================================================
   TOOL SEARCH
============================================================ */
const searchInput = $('#toolSearch');
const toolsGrid = $('#toolsGrid');
const cards = $$('.tool-card');
let noResults = null;

searchInput.addEventListener('input', () => {
  const q = searchInput.value.trim().toLowerCase();
  let visible = 0;

  cards.forEach(card => {
    const text = (card.textContent + ' ' + (card.dataset.tags || '')).toLowerCase();
    const match = !q || text.includes(q);
    card.classList.toggle('hide', !match);
    if(match) visible++;
  });

  if(noResults) { noResults.remove(); noResults = null; }
  if(visible === 0){
    noResults = document.createElement('div');
    noResults.className = 'no-results';
    noResults.textContent = '🔍 No tools match "' + searchInput.value + '". Try another keyword.';
    toolsGrid.appendChild(noResults);
  }
});

/* ============================================================
   1. CALCULATOR
============================================================ */
const calcState = { current: '0', previous: null, op: null, resetNext: false };

const calcCurrentEl = $('#calcCurrent');
const calcExprEl = $('#calcExpr');

function calcRender(){
  calcCurrentEl.textContent = calcState.current;
  calcExprEl.textContent = calcState.previous !== null
    ? calcState.previous + ' ' + (calcState.op || '')
    : '';
}

function calcFmt(n){
  if(!isFinite(n)) return 'Error';
  const s = parseFloat(n.toPrecision(12)).toString();
  return s.length > 16 ? parseFloat(n.toFixed(8)).toString() : s;
}

function calcCompute(a, b, op){
  switch(op){
    case '+': return a + b;
    case '−': return a - b;
    case '×': return a * b;
    case '÷': return b === 0 ? NaN : a / b;
    default:  return b;
  }
}

function calcNum(d){
  if(calcState.current === 'Error'){ calcReset(); }
  if(calcState.resetNext){ calcState.current = '0'; calcState.resetNext = false; }

  if(d === '.'){
    if(!calcState.current.includes('.')) calcState.current += '.';
  } else {
    if(calcState.current === '0') calcState.current = d;
    else calcState.current += d;
  }
  if(calcState.current.replace('-','').replace('.','').length > 15){
    calcState.current = calcState.current.slice(0, -1);
  }
  calcRender();
}

function calcOperator(op){
  const cur = parseFloat(calcState.current);
  if(isNaN(cur)) return;

  if(calcState.op !== null && calcState.previous !== null && !calcState.resetNext){
    const res = calcCompute(calcState.previous, cur, calcState.op);
    calcState.current = calcFmt(res);
    calcState.previous = res;
  } else {
    calcState.previous = cur;
  }
  calcState.op = op;
  calcState.resetNext = true;
  calcRender();
}

function calcEquals(){
  if(calcState.op === null || calcState.previous === null) return;
  const cur = parseFloat(calcState.current);
  if(isNaN(cur)) return;

  const res = calcCompute(calcState.previous, cur, calcState.op);
  calcExprEl.textContent = calcState.previous + ' ' + calcState.op + ' ' + cur + ' =';
  calcState.current = calcFmt(res);
  calcState.previous = null;
  calcState.op = null;
  calcState.resetNext = true;
  calcCurrentEl.textContent = calcState.current;
  setTimeout(() => { if(!calcState.op) calcExprEl.textContent = ''; }, 1600);
}

function calcReset(){
  calcState.current = '0';
  calcState.previous = null;
  calcState.op = null;
  calcState.resetNext = false;
  calcRender();
}

function calcBack(){
  if(calcState.resetNext){ calcReset(); return; }
  calcState.current = calcState.current.length > 1
    ? calcState.current.slice(0, -1)
    : '0';
  if(calcState.current === '-') calcState.current = '0';
  calcRender();
}

function calcPercent(){
  const cur = parseFloat(calcState.current);
  if(isNaN(cur)) return;
  const base = calcState.previous !== null ? calcState.previous : 1;
  calcState.current = calcFmt(base * cur / 100);
  calcRender();
}

function calcSign(){
  if(calcState.current === '0' || calcState.current === 'Error') return;
  calcState.current = calcState.current.startsWith('-')
    ? calcState.current.slice(1)
    : '-' + calcState.current;
  calcRender();
}

$('#calcPad').addEventListener('click', (e) => {
  const btn = e.target.closest('button');
  if(!btn) return;

  if(btn.dataset.num !== undefined) return calcNum(btn.dataset.num);
  if(btn.dataset.op  !== undefined) return calcOperator(btn.dataset.op);

  switch(btn.dataset.fn){
    case 'ac':   calcReset(); break;
    case 'back': calcBack(); break;
    case 'pct':  calcPercent(); break;
    case 'sign': calcSign(); break;
    case 'eq':   calcEquals(); break;
  }
});

/* keyboard support while calculator modal open */
document.addEventListener('keydown', (e) => {
  if(!openModalEl || openModalEl.id !== 'modal-calc') return;
  const k = e.key;

  if(/^[0-9]$/.test(k)){ calcNum(k); e.preventDefault(); }
  else if(k === '.'){ calcNum('.'); e.preventDefault(); }
  else if(k === '+'){ calcOperator('+'); e.preventDefault(); }
  else if(k === '-'){ calcOperator('−'); e.preventDefault(); }
  else if(k === '*'){ calcOperator('×'); e.preventDefault(); }
  else if(k === '/'){ calcOperator('÷'); e.preventDefault(); }
  else if(k === '%'){ calcPercent(); e.preventDefault(); }
  else if(k === 'Enter' || k === '='){ calcEquals(); e.preventDefault(); }
  else if(k === 'Backspace'){ calcBack(); e.preventDefault(); }
  else if(k === 'Delete'){ calcReset(); e.preventDefault(); }
});

calcRender();

/* ============================================================
   2. IMAGE COMPRESSOR
============================================================ */
let imgFile = null;
let imgBlob = null;

const imgDrop     = $('#imgDrop');
const imgInput    = $('#imgInput');
const imgPanel    = $('#imgPanel');
const imgPreview  = $('#imgPreview');
const imgQuality  = $('#imgQuality');
const imgWidth    = $('#imgWidth');
const imgFormat   = $('#imgFormat');
const imgRun      = $('#imgRun');

imgDrop.addEventListener('click', () => imgInput.click());

['dragenter','dragover'].forEach(ev =>
  imgDrop.addEventListener(ev, e => { e.preventDefault(); imgDrop.classList.add('drag'); })
);
['dragleave','drop'].forEach(ev =>
  imgDrop.addEventListener(ev, e => { e.preventDefault(); imgDrop.classList.remove('drag'); })
);
imgDrop.addEventListener('drop', e => {
  const f = e.dataTransfer.files[0];
  if(f && f.type.startsWith('image/')) loadImage(f);
  else toast('Please drop a valid image file', 'error');
});

imgInput.addEventListener('change', () => {
  if(imgInput.files[0]) loadImage(imgInput.files[0]);
});

imgQuality.addEventListener('input', () => imgQualityVal.textContent = imgQuality.value);
imgWidth.addEventListener('input',   () => imgWidthVal.textContent   = imgWidth.value);

function loadImage(file){
  imgFile = file;
  imgBlob = null;
  imgPanel.style.display = 'block';
  $('#imgResult').style.display = 'none';

  const url = URL.createObjectURL(file);
  imgPreview.src = url;
  imgPreview.onload = () => URL.revokeObjectURL(url);

  compressImage();
}

function compressImage(){
  if(!imgFile) return;

  const reader = new FileReader();
  reader.onload = (ev) => {
    const img = new Image();
    img.onload = () => {
      const maxW = parseInt(imgWidth.value, 10);
      let w = img.naturalWidth, h = img.naturalHeight;

      if(w > maxW){
        h = Math.round(h * maxW / w);
        w = maxW;
      }

      const canvas = document.createElement('canvas');
      canvas.width = w;
      canvas.height = h;
      const ctx = canvas.getContext('2d');
      ctx.imageSmoothingEnabled = true;
      ctx.imageSmoothingQuality = 'high';

      const type = imgFormat.value;
      if(type === 'image/jpeg'){
        ctx.fillStyle = '#ffffff';
        ctx.fillRect(0, 0, w, h);
      }
      ctx.drawImage(img, 0, 0, w, h);

      const quality = parseInt(imgQuality.value, 10) / 100;

      canvas.toBlob((blob) => {
        if(!blob){ toast('Compression failed', 'error'); return; }
        imgBlob = blob;
        showImageResult(imgFile.size, blob.size, w, h);
      }, type, quality);
    };
    img.src = ev.target.result;
  };
  reader.readAsDataURL(imgFile);
}

function showImageResult(origSize, newSize, w, h){
  $('#imgOrigSize').textContent = formatBytes(origSize);
  $('#imgNewSize').textContent  = formatBytes(newSize);

  const saved = origSize - newSize;
  const pct = ((saved / origSize) * 100).toFixed(1);
  const line = $('#imgSaveLine');

  if(saved > 0){
    line.innerHTML = '<span style="color:var(--success);font-weight:700">▼ ' +
      pct + '% smaller</span> · saved ' + formatBytes(saved) +
      ' · dimensions ' + w + '×' + h;
  } else {
    line.innerHTML = '<span style="color:var(--warning);font-weight:700">No size reduction</span> — try lowering quality or format.';
  }

  $('#imgResult').style.display = 'block';
}

imgRun.addEventListener('click', () => {
  if(!imgFile){ toast('Choose an image first', 'error'); return; }
  compressImage();
  toast('Image compressed!', 'success');
});

$('#imgDownload').addEventListener('click', () => {
  if(!imgBlob){ toast('Nothing to download', 'error'); return; }
  const ext = imgFormat.value === 'image/webp' ? 'webp' : 'jpg';
  const base = (imgFile.name || 'image').replace(/\.[^.]+$/, '');
  const a = document.createElement('a');
  a.href = URL.createObjectURL(imgBlob);
  a.download = base + '-compressed.' + ext;
  a.click();
  setTimeout(() => URL.revokeObjectURL(a.href), 2000);
  toast('Download started', 'success');
});

/* ============================================================
   3. PDF COMPRESSOR
============================================================ */
let pdfFile = null;
let pdfBlob = null;

const pdfDrop = $('#pdfDrop');
const pdfInput = $('#pdfInput');
const pdfPanel = $('#pdfPanel');

pdfDrop.addEventListener('click', () => pdfInput.click());

['dragenter','dragover'].forEach(ev =>
  pdfDrop.addEventListener(ev, e => { e.preventDefault(); pdfDrop.classList.add('drag'); })
);
['dragleave','drop'].forEach(ev =>
  pdfDrop.addEventListener(ev, e => { e.preventDefault(); pdfDrop.classList.remove('drag'); })
);
pdfDrop.addEventListener('drop', e => {
  const f = e.dataTransfer.files[0];
  if(f && f.type === 'application/pdf') compressPDF(f);
  else toast('Please drop a PDF file', 'error');
});

pdfInput.addEventListener('change', () => {
  if(pdfInput.files[0]) compressPDF(pdfInput.files[0]);
});

async function compressPDF(file){
  pdfFile = file;
  pdfPanel.style.display = 'block';
  pdfBlob = null;
  $('#pdfWarn').style.display = 'none';

  if(typeof PDFLib === 'undefined'){
    toast('PDF library failed to load. Check your connection.', 'error');
    $('#pdfOrigSize').textContent = formatBytes(file.size);
    $('#pdfNewSize').textContent = 'Unavailable';
    return;
  }

  $('#pdfOrigSize').textContent = formatBytes(file.size);
  $('#pdfNewSize').textContent = 'Processing…';
  $('#pdfSaveLine').textContent = '';

  try{
    const bytes = await file.arrayBuffer();
    const doc = await PDFLib.PDFDocument.load(bytes, { ignoreEncryption: true, updateMetadata: false });

    // strip metadata to save space
    try{
      doc.setTitle('');
      doc.setAuthor('');
      doc.setSubject('');
      doc.setKeywords([]);
      doc.setProducer('');
      doc.setCreator('');
    }catch(e){ /* some docs disallow */ }

    const out = await doc.save({ useObjectStreams: true, addDefaultPage: false });
    const optimized = new Blob([out], { type: 'application/pdf' });

    const origSize = file.size;
    const newSize = optimized.size;
    const saved = origSize - newSize;

    if(saved > 0){
      pdfBlob = optimized;
      $('#pdfNewSize').textContent = formatBytes(newSize);
      $('#pdfSaveLine').innerHTML = '<span style="color:var(--success);font-weight:700">▼ ' +
        ((saved / origSize) * 100).toFixed(1) + '% smaller</span> · saved ' + formatBytes(saved);
    } else {
      pdfBlob = file;
      $('#pdfNewSize').textContent = formatBytes(origSize);
      $('#pdfSaveLine').innerHTML = '<span style="color:var(--warning);font-weight:700">Already optimized</span> — the original is the smallest version.';
      $('#pdfWarn').style.display = 'block';
    }
    toast('PDF processed!', 'success');

  }catch(err){
    console.error(err);
    $('#pdfNewSize').textContent = 'Failed';
    $('#pdfSaveLine').innerHTML = '<span style="color:var(--danger)">Could not process this PDF (it may be encrypted or corrupted).</span>';
    toast('PDF processing failed', 'error');
  }
}

$('#pdfDownload').addEventListener('click', () => {
  if(!pdfBlob){ toast('Nothing to download', 'error'); return; }
  const a = document.createElement('a');
  a.href = URL.createObjectURL(pdfBlob);
  a.download = (pdfFile.name || 'document').replace(/\.pdf$/i, '') + '-optimized.pdf';
  a.click();
  setTimeout(() => URL.revokeObjectURL(a.href), 2000);
  toast('Download started', 'success');
});

/* ============================================================
   4. AI ASSISTANT
============================================================ */
const aiKey    = $('#aiKey');
const aiBase   = $('#aiBase');
const aiModel  = $('#aiModel');
const aiTask   = $('#aiTask');
const aiInput  = $('#aiInput');
const aiOutput = $('#aiOutput');
const aiRun    = $('#aiRun');

// restore settings
aiKey.value   = localStorage.getItem('nexus-ai-key')   || '';
aiBase.value  = localStorage.getItem('nexus-ai-base')  || 'https://api.openai.com/v1';
aiModel.value = localStorage.getItem('nexus-ai-model') || 'gpt-4o-mini';

$('#aiSave').addEventListener('click', () => {
  localStorage.setItem('nexus-ai-key', aiKey.value.trim());
  localStorage.setItem('nexus-ai-base', aiBase.value.trim());
  localStorage.setItem('nexus-ai-model', aiModel.value.trim());
  toast('AI settings saved', 'success');
});

aiRun.addEventListener('click', async () => {
  const text = aiInput.value.trim();
  const key = aiKey.value.trim();

  if(!text){ toast('Enter some text first', 'error'); aiInput.focus(); return; }
  if(!key){
    aiOutput.classList.remove('placeholder');
    aiOutput.innerHTML =
      '⚠️ <b>No API key set.</b>\n\n' +
      'Open "API Settings" above and paste an OpenAI-compatible API key.\n\n' +
      'Supported providers:\n' +
      '• OpenAI — https://api.openai.com/v1\n' +
      '• Groq — https://api.groq.com/openai/v1\n' +
      '• OpenRouter — https://openrouter.ai/api/v1\n' +
      '• Together — https://api.together.xyz/v1\n\n' +
      'Your key is stored only in this browser and is sent directly to your chosen provider.';
    return;
  }

  const base = aiBase.value.trim().replace(/\/+$/, '');
  const model = aiModel.value.trim() || 'gpt-4o-mini';
  const systemPrompt = aiTask.value || 'You are a helpful, concise assistant.';

  aiRun.disabled = true;
  aiRun.innerHTML = '<span class="spinner"></span> Thinking…';
  aiOutput.classList.add('placeholder');
  aiOutput.textContent = 'Generating response…';

  try{
    const res = await fetch(base + '/chat/completions', {
      method: 'POST',
      headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer ' + key
      },
      body: JSON.stringify({
        model: model,
        messages: [
          { role: 'system', content: systemPrompt },
          { role: 'user', content: text }
        ],
        temperature: 0.7,
        max_tokens: 1000
      })
    });

    if(!res.ok){
      const errText = await res.text();
      throw new Error('HTTP ' + res.status + ' — ' + errText.slice(0, 220));
    }

    const data = await res.json();
    const reply = data?.choices?.[0]?.message?.content;

    if(!reply) throw new Error('Empty response from provider.');

    aiOutput.classList.remove('placeholder');
    aiOutput.textContent = reply;
    toast('AI response ready', 'success');

  }catch(err){
    console.error(err);
    aiOutput.classList.remove('placeholder');
    aiOutput.innerHTML = '❌ <b>Request failed</b>\n\n' + String(err.message || err) +
      '\n\nCheck your API key, base URL, model name and network connection.';
    toast('AI request failed', 'error');
  }finally{
    aiRun.disabled = false;
    aiRun.textContent = '✨ Run AI';
  }
});

/* ============================================================
   5. QR CODE GENERATOR
============================================================ */
const qrText = $('#qrText');
const qrSize = $('#qrSize');
const qrMargin = $('#qrMargin');
const qrImg = $('#qrImg');
const qrResult = $('#qrResult');

$('#qrRun').addEventListener('click', () => {
  const data = qrText.value.trim();
  if(!data){ toast('Enter some content first', 'error'); qrText.focus(); return; }

  const size = qrSize.value;
  const margin = qrMargin.value;
  const url = 'https://api.qrserver.com/v1/create-qr-code/?size=' + size + 'x' + size +
              '&margin=' + margin + '&data=' + encodeURIComponent(data);

  qrImg.src = url;
  qrResult.style.display = 'block';
  toast('QR code generated', 'success');
});

$('#qrDownload').addEventListener('click', async () => {
  if(!qrImg.src){ toast('Generate a QR code first', 'error'); return; }
  try{
    const res = await fetch(qrImg.src);
    const blob = await res.blob();
    const a = document.createElement('a');
    a.href = URL.createObjectURL(blob);
    a.download = 'qr-code.png';
    a.click();
    setTimeout(() => URL.revokeObjectURL(a.href), 2000);
    toast('Download started', 'success');
  }catch(e){
    window.open(qrImg.src, '_blank');
    toast('Opened in new tab — right-click to save', 'success');
  }
});

/* ============================================================
   6. PASSWORD GENERATOR
============================================================ */
const pwOptions = { upper: true, lower: true, num: true, sym: true };
const pwLen = $('#pwLen');
const pwOutput = $('#pwOutput');
const pwMeter = $('#pwMeter');
const pwLabel = $('#pwLabel');

const CHARS = {
  upper: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
  lower: 'abcdefghijklmnopqrstuvwxyz',
  num:   '0123456789',
  sym:   '!@#$%^&*()_+-=[]{}|;:,.<>?'
};

pwLen.addEventListener('input', () => {
  $('#pwLenVal').textContent = pwLen.value;
});

$$('[data-pw]').forEach(chip => {
  chip.addEventListener('click', () => {
    const key = chip.dataset.pw;
    const active = Object.values(pwOptions).filter(Boolean).length;

    if(pwOptions[key] && active === 1){
      toast('At least one character set is required', 'error');
      return;
    }
    pwOptions[key] = !pwOptions[key];
    chip.classList.toggle('active', pwOptions[key]);
    generatePassword();
  });
});

function generatePassword(){
  const sets = Object.keys(pwOptions).filter(k => pwOptions[k]).map(k => CHARS[k]);
  if(sets.length === 0) return;

  const all = sets.join('');
  const len = parseInt(pwLen.value, 10);
  const bytes = new Uint32Array(len);
  crypto.getRandomValues(bytes);

  let pw = '';
  for(let i = 0; i < len; i++){
    pw += all[bytes[i] % all.length];
  }

  pwOutput.textContent = pw;
  updateStrength(pw, sets.length);
}

function updateStrength(pw, setCount){
  let score = 0;
  score += Math.min(pw.length * 2.5, 50);
  score += setCount * 10;
  if(/[A-Z]/.test(pw)) score += 5;
  if(/[0-9]/.test(pw)) score += 5;
  if(/[^A-Za-z0-9]/.test(pw)) score += 8;
  score = Math.min(Math.round(score), 100);

  let color, label;
  if(score < 35){ color = '#ef4444'; label = 'Weak'; }
  else if(score < 60){ color = '#f59e0b'; label = 'Fair'; }
  else if(score < 82){ color = '#22d3ee'; label = 'Strong'; }
  else { color = '#10b981'; label = 'Very Strong'; }

  pwMeter.style.width = score + '%';
  pwMeter.style.background = color;
  pwLabel.textContent = label + ' · ' + score + '/100';
  pwLabel.style.color = color;
}

$('#pwGen').addEventListener('click', () => {
  generatePassword();
  toast('New password generated', 'success');
});

$('#pwCopy').addEventListener('click', () => {
  const pw = pwOutput.textContent;
  if(!pw || pw === 'Click Generate'){ toast('Generate a password first', 'error'); return; }
  copyText(pw);
});

generatePassword();

/* ============================================================
   7. UNIT CONVERTER
============================================================ */
const UNITS = {
  length: {
    'Meter (m)': 1,
    'Kilometer (km)': 1000,
    'Centimeter (cm)': 0.01,
    'Millimeter (mm)': 0.001,
    'Mile (mi)': 1609.344,
    'Yard (yd)': 0.9144,
    'Foot (ft)': 0.3048,
    'Inch (in)': 0.0254
  },
  weight: {
    'Kilogram (kg)': 1,
    'Gram (g)': 0.001,
    'Milligram (mg)': 0.000001,
    'Metric Ton (t)': 1000,
    'Pound (lb)': 0.45359237,
    'Ounce (oz)': 0.028349523125
  },
  data: {
    'Byte (B)': 0.000001,
    'Kilobyte (KB)': 0.001,
    'Megabyte (MB)': 1,
    'Gigabyte (GB)': 1000,
    'Terabyte (TB)': 1000000
  },
  temp: {
    'Celsius (°C)': 'c',
    'Fahrenheit (°F)': 'f',
    'Kelvin (K)': 'k'
  }
};

let currentCat = 'length';

const convFrom = $('#convFrom');
const convTo = $('#convTo');
const convValue = $('#convValue');
const convResult = $('#convResult');

function populateUnits(){
  const units = Object.keys(UNITS[currentCat]);
  convFrom.innerHTML = '';
  convTo.innerHTML = '';
  units.forEach((u, i) => {
    convFrom.add(new Option(u, u));
    convTo.add(new Option(u, u));
  });
  convFrom.selectedIndex = 0;
  convTo.selectedIndex = Math.min(1, units.length - 1);
  convert();
}

function convertTemp(v, from, to){
  let c;
  if(from === 'c') c = v;
  else if(from === 'f') c = (v - 32) * 5 / 9;
  else c = v - 273.15;

  if(to === 'c') return c;
  if(to === 'f') return c * 9 / 5 + 32;
  return c + 273.15;
}

function convert(){
  const v = parseFloat(convValue.value);
  if(isNaN(v)){ convResult.textContent = '—'; return; }

  const f = convFrom.value;
  const t = convTo.value;
  let out;

  if(currentCat === 'temp'){
    out = convertTemp(v, UNITS.temp[f], UNITS.temp[t]);
  } else {
    const table = UNITS[currentCat];
    out = v * table[f] / table[t];
  }

  let display;
  if(!isFinite(out)) display = '—';
  else if(Math.abs(out) !== 0 && (Math.abs(out) < 0.000001 || Math.abs(out) >= 1e12)) display = out.toExponential(6);
  else display = parseFloat(out.toFixed(10)).toLocaleString(undefined, { maximumFractionDigits: 10 });

  convResult.textContent = display + ' ' + t.replace(/.*\(([^)]+)\)/, '$1');
}

$$('#convCats .chip').forEach(chip => {
  chip.addEventListener('click', () => {
    $$('#convCats .chip').forEach(c => c.classList.remove('active'));
    chip.classList.add('active');
    currentCat = chip.dataset.cat;
    populateUnits();
  });
});

convValue.addEventListener('input', convert);
convFrom.addEventListener('change', convert);
convTo.addEventListener('change', convert);

populateUnits();

/* ============================================================
   8. TEXT TOOLS
============================================================ */
const textArea = $('#textArea');

function updateTextStats(){
  const t = textArea.value;
  const words = t.trim() ? t.trim().split(/\s+/).length : 0;
  const chars = t.length;
  const sentences = t.trim() ? (t.match(/[.!?]+(\s|$)/g) || []).length || (t.trim() ? 1 : 0) : 0;
  const minutes = Math.max(1, Math.ceil(words / 200));

  $('#tWords').textContent = words.toLocaleString();
  $('#tChars').textContent = chars.toLocaleString();
  $('#tSent').textContent  = sentences.toLocaleString();
  $('#tRead').textContent  = words === 0 ? '0m' : minutes + 'm';
}

textArea.addEventListener('input', updateTextStats);

$$('[data-tx]').forEach(chip => {
  chip.addEventListener('click', () => {
    const action = chip.dataset.tx;
    let t = textArea.value;

    switch(action){
      case 'upper':    t = t.toUpperCase(); break;
      case 'lower':    t = t.toLowerCase(); break;
      case 'title':    t = t.replace(/\w\S*/g, w => w.charAt(0).toUpperCase() + w.slice(1).toLowerCase()); break;
      case 'sentence': t = t.toLowerCase().replace(/(^\s*\w|[.!?]\s+\w)/g, c => c.toUpperCase()); break;
      case 'trim':     t = t.replace(/[ \t]+/g, ' ').replace(/\n{3,}/g, '\n\n').trim(); break;
      case 'reverse':  t = t.split('').reverse().join(''); break;
      case 'clear':    t = ''; break;
      case 'copy':
        if(!t){ toast('Nothing to copy', 'error'); return; }
        copyText(t);
        return;
    }

    textArea.value = t;
    updateTextStats();
    if(action !== 'clear') toast('Text transformed', 'success');
  });
});

updateTextStats();

/* ============================================================
   SMOOTH SCROLL FOR ANCHORS
============================================================ */
$$('a[href^="#"]').forEach(a => {
  a.addEventListener('click', (e) => {
    const id = a.getAttribute('href');
    if(id === '#') return;
    const target = document.querySelector(id);
    if(target){
      e.preventDefault();
      target.scrollIntoView({ behavior: 'smooth', block: 'start' });
    }
  });
});

})();
</script>
</body>
</html>
Tools, Workflow & User Experience
Here's how the main pieces fit together and what you can do with each one.

Tool discovery & navigation: A search bar filters the tool cards by keyword, and every card opens a modal with the specific tool. The sticky navigation and smooth scrolling keep everything accessible.

