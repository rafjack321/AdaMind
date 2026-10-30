# AdaMind & CortexDB (v0.2.1) — Handbook & Tutorial

**High-Speed In-Browser Neuro-RAG Knowledge Database & Cognitive Neocortex Modeling Language**

*License: Dual-Licensed under `MIT OR Apache-2.0` (Open Source, locally executable & content-agnostic)*

---

## Table of Contents

1. [Overview: What is AdaMind CortexDB?](#1-overview-what-is-adamind-cortexdb)
2. [Quick Start in 60 Seconds](#2-quick-start-in-60-seconds)
3. [Step-by-Step Tutorial: Working with CortexDB in the Browser](#3-step-by-step-tutorial-working-with-cortexdb-in-the-browser)
   * [Step 1: Importing Documents & Web Pages (.pdf, .epub, .md, .txt, URL)](#step-1-importing-documents--web-pages-pdf-epub-md-txt-url)
   * [Step 2: Connecting AI Models & API Keys (Free AI, Gemini, Copilot)](#step-2-connecting-ai-models--api-keys-free-ai-gemini-copilot)
   * [Step 3: Asking Questions — Local Knowledge, Live Online Search & Real-Time Search](#step-3-asking-questions--local-knowledge-live-online-search--real-time-search)
   * [Step 4: Cortex Telemetry, Sleep Consolidation (NREM/REM) & Benchmarking](#step-4-cortex-telemetry-sleep-consolidation-nremrem--benchmarking)
   * [Step 5: 60-Second Auto-Save, Backups & Zero-Wipe Security](#step-5-60-second-auto-save-backups--zero-wipe-security)
4. [Developer Tutorial: The AdaMind Language (.adm) & Python Runtime](#4-developer-tutorial-the-adamind-language-adm--python-runtime)
   * [Neurobiological Mathematics & Hybrid Retrieval Formulas](#neurobiological-mathematics--hybrid-retrieval-formulas)
   * [Designing a Custom AdaMind Module](#designing-a-custom-adamind-module)
   * [Running the Python Reference Runtime & IsolatedBridge v1.1](#running-the-python-reference-runtime--isolatedbridge-v11)
5. [Frequently Asked Questions & Troubleshooting](#5-frequently-asked-questions--troubleshooting)
6. [License & Contributing](#6-license--contributing)

---

## 1. Overview: What is AdaMind CortexDB?

**AdaMind CortexDB** combines principles from computational neuroscience with modern information retrieval (*Retrieval-Augmented Generation*, RAG) inside a single, zero-backend browser application (`index.html`):

* **Sub-Millisecond Hybrid Search ($< 1\,\text{ms}$):** Every text passage is indexed simultaneously into a fault-tolerant $2048\text{-bit}$ **Sparse Distributed Representation (SDR)** bit-index with exactly $k = 41$ active minicolumns ($2\,\%$ sparsity) and a lexical **BM25+ full-text index**.
* **Client-Side Multi-Format Ingestion:** Parses `.pdf` (with exact page numbers), `.epub` (chapter-by-chapter following the `.opf` spine), `.md`, `.txt`, live web URLs (`https://...`), and free-text notes directly in your browser's memory—your files never need to be uploaded to a third-party ingestion server.
* **Flexible AI Synthesis:** Ready to use out of the box via the built-in **Free AI** cascade (including a $100\,\%$ offline local fallback) or connectable to **Google Gemini** and **GitHub / Microsoft Copilot** using your own API key.
* **Cortical Memory Dynamics:** Features a $7$-slot NMDA working memory buffer, acetylcholine and dopamine neuromodulation, two-stage sleep consolidation (NREM/REM), automatic persistence every $60\,\text{s}$ in `IndexedDB`, and deterministic `Zero-Wipe` memory sanitization for sensitive sessions.

---

## 2. Quick Start in 60 Seconds

### Option A: Direct Launch (Zero Setup)

Double-click `index.html` to open it in any modern browser (Chrome, Edge, Firefox, or Safari). On first launch, CortexDB automatically indexes three pre-installed technical reference documents into local memory.

### Option B: Local HTTP Server (Recommended for Large PDF/EPUB Collections)

Run a lightweight local HTTP server in your project directory:

```bash
# Using Python 3
python3 -m http.server 8080
```

Then open your browser and navigate to:

```text
http://localhost:8080/index.html
```

**Your First Test in 3 Clicks:**

1. In the center column, click one of the starter prompt buttons (e.g., explaining SDRs & Free Energy).
2. Watch the **AdaMind Cortex Telemetry** panel in the upper-right column as the $64 \times 32$ minicolumn matrix activates and Variational Free Energy ($F$) converges.
3. In the generated answer, click any cyan citation badge such as `[Quelle: AdaMind_Sprachspezifikation_v0.2.md, ...]` to jump directly to the highlighted original passage inside the **Source Inspector** on the right.

---

## 3. Step-by-Step Tutorial: Working with CortexDB in the Browser

### Step 1: Importing Documents & Web Pages (.pdf, .epub, .md, .txt, URL)

In the **left column**, locate the **Multi-Format Knowledge Import** (*Multi-Format Wissens-Import*) panel:

1. **Drag & Drop File Ingestion:**
   * Drag one or multiple files onto the dashed drop zone (or click it to open the file picker).
   * **Supported Formats:**
     * `.pdf`: Extracts text page by page via `pdf.js` and preserves exact page numbers (`S. 1`, `S. 2`, ...) for accurate citations.
     * `.epub`: Unpacks the e-book archive in-memory via `JSZip`, reads `META-INF/container.xml` and the `.opf` reading spine, and extracts clean chapter headings.
     * `.md` / `.markdown`: Splits documents structurally along Markdown headings (`#` through `####`).
     * `.txt`: Segments plain-text documents cleanly along paragraph and sentence boundaries.
   * **Smart Overlapping Chunking:** Long sections are automatically divided into chunks of roughly $700\text{--}950$ characters with a $150$-character overlap so semantic context is never lost across boundaries.

2. **Direct Webpage Indexing via URL:**
   * Paste a complete URL (e.g., `https://en.wikipedia.org/wiki/Neocortex`) into the URL field and click **Load** (*Laden*).
   * The page content is extracted, chunked, and stored permanently as a `WEB` document in your database.

3. **Adding Custom Notes:**
   * Expand the free-text/Markdown note drawer (*Freitext / Markdown-Notiz einfügen*), enter a title and body text or code, and click the index button (*In SDR + BM25+ indizieren*).

4. **Filtering Active Sources (Document Explorer):**
   * Below the importer, the **Document Explorer** lists every loaded document with an individual checkbox.
   * Unchecking a document excludes it in $O(1)$ time from all searches and AI prompts without deleting it. Clicking a document's title previews its chunks in the right-hand Source Inspector.

### Step 2: Connecting AI Models & API Keys (Free AI, Gemini, Copilot)

Click **AI & API Keys** (*KI & API-Keys*) in the top-right header bar (or click the **Active AI Core** KPI pill) to open the configuration dialog. Three provider modes are available:

#### A. Free AI (Ready Immediately — No API Key Required)

Ideal for instant use without registration. Choose from three execution strategies:

* **Auto-Cascade (Default):** Attempts the integrated low-latency Gemini bridge first, falls back to the free CORS-enabled OpenAI-compatible cloud endpoint, and seamlessly switches to the local synthesizer if offline.
* **Direct (Free Cloud Endpoint):** Sends retrieved RAG chunks to the free OpenAI-compatible endpoint `text.pollinations.ai/openai`.
* **100% Offline (Local AdaMind Neuro-Synthesizer):** Zero bytes leave your machine. The deterministic local synthesizer ranks sentences across retrieved chunks by stem density and SDR salience to assemble a fully cited summary.

#### B. Google Gemini (Using Your Own API Key)

1. Select the **Google Gemini** card.
2. Enter your Google AI Studio key (`AIzaSy...`). Use the eye icon to verify your input.
3. Pick a preset model (`gemini-3-flash-preview`, `gemini-2.5-flash`, or `gemini-2.5-pro`) or type any custom model ID into the right-hand field.
4. Keep **Google Search Grounding (`google_search`)** checked so Gemini can enrich answers with verified live Google Search sources whenever Online Search is enabled.

#### C. GitHub / Microsoft Copilot & OpenAI-Compatible Gateways

1. Select the **GitHub / Copilot** card.
2. Enter your Bearer API key or Personal Access Token (`github_pat_...`, `ghu_...`, or `sk-...`).
3. Choose an **Endpoint Profile**:
   * `https://models.github.ai/inference/chat/completions`: **Recommended for direct browser usage**, as it natively supports browser CORS requests (e.g., with `gpt-4o` or `gpt-4.1`).
   * `https://api.githubcopilot.com/chat/completions`: Includes automatic token exchange for `ghu_`/`gho_` tokens (may require a local CORS proxy depending on browser security policies).
   * `https://api.openai.com/v1/chat/completions`: Compatible with standard OpenAI API keys or self-hosted local LLM servers (such as Ollama, LM Studio, or vLLM by editing the endpoint URL).

4. **Test Connection & Activate:**
   * Click **Test Connection** (*Verbindung prüfen*) to run a live authentication and latency ping.
   * Click **Apply & Activate** (*Übernehmen & Aktivieren*). When *Remember settings & keys locally in browser* is checked, your configuration is persisted locally inside `IndexedDB`.

### Step 3: Asking Questions — Local Knowledge, Live Online Search & Real-Time Search

The **center column** lets you switch seamlessly between AI-synthesized answers and sub-millisecond raw retrieval:

#### Mode 1: AI Synthesis + RAG (Default View)

1. **Combine Knowledge Sources Below the Chat Stream:**
   * **Database Knowledge (Local)** (*Datenbank-Wissen*): Searches your enabled local documents via Hybrid SDR + BM25+ retrieval.
   * **Online Content (Live Web Search)** (*Online-Inhalt*): Simultaneously queries English and German Wikipedia, DuckDuckGo Instant Answers, and peer-reviewed scholarly metadata via **Crossref**.
   * **Pro Tip — Paste URLs Directly Into Your Question:** If you include an `https://` link inside your question while Online Content is active, CortexDB fetches and reads that web page live and cross-references it against your local documents.
2. **Select Context Depth:** Choose **Top 4**, **Top 6**, or **Top 10 Chunks** from the dropdown menu.
3. **Submit Your Question:** Press `Enter` to send (use `Shift + Enter` for a line break).
4. **Verify Citations:**
   * Local facts display clickable cyan badges: `[Quelle: Filename, S. X]`.
   * Web facts display clickable violet badges: `[Web: Title]`.
   * All retrieved passages appear immediately in the right-hand **Source Inspector** with query terms highlighted—even before the AI finishes generating text.

#### Mode 2: Real-Time Vector Search ($< 1\,\text{ms}$)

Click the **Real-Time Vector Search (<1ms)** (*Echtzeit-Vektorsuche*) tab at the top of the center column:

* Every keystroke searches thousands of chunks in $0.05\,\text{ms}$ to $0.80\,\text{ms}$ ($50\text{--}800\,\mu\text{s}$) with zero LLM latency.
* Character $3$-gram shingles inside the $2048\text{-bit}$ SDR encoder combine with stem-normalized BM25+ scoring to match exact technical terms, numbers, compound words, and even typos.
* Click **Analyze in AI Chat** (*-> Im KI-Chat analysieren*) underneath any hit to hand that passage straight over to the RAG chat.

### Step 4: Cortex Telemetry, Sleep Consolidation (NREM/REM) & Benchmarking

The **right column** visualizes AdaMind's internal neurophysiological state in real time:

* **$64 \times 32$ SDR Matrix ($2048$ Minicolumns):**
  * **Cyan (`Match`):** Minicolumns active in both your query and the top-ranked database chunk.
  * **Rose ($\ominus^+$ `On-Error`):** Unexpected query features absent from the top prior.
  * **Amber ($\ominus^-$ `Off-Error`):** Features predicted by the stored memory chunk that were omitted in the query (*Omission Response*).
* **Neuromodulators & Working Memory:**
  * **ACh Precision ($\Pi$):** Rises with prediction error to amplify bottom-up sensory evidence.
  * **Dopamine (Salience):** Tracks retrieval confidence and gates memory prioritization.
  * **NMDA Working Memory ($0/7$):** Maintains up to $7$ recently active chunks via recurrent excitation. Clicking any slot chip opens that passage in the Source Inspector.
* **Sleep Consolidation (`Schlaf (NREM/REM)` in Top Header):**
  * Potentiates all chunks currently held in working memory via Hebbian Long-Term Potentiation (`ltpWeights`, up to $1.6\times$) while applying homeostatic synaptic downscaling ($\times 0.92$ toward the $1.0$ baseline) across the remaining corpus. Frequently accessed core knowledge naturally rises in future rankings.
* **High-Speed Benchmark (`+1.000 Chunks` in Top Header):**
  * Generates and dual-indexes $1,000$ synthetic neuroscience/systems chunks on the fly and measures both ingestion throughput and hybrid query latency in microseconds.

### Step 5: 60-Second Auto-Save, Backups & Zero-Wipe Security

1. **Automatic Saving Every 60 Seconds (`IndexedDB`):**
   * Whenever **Local Persistence (`IndexedDB`)** is enabled at the bottom left, a background scheduler atomically saves all documents, active source filters, and learned LTP synaptic weights every $60\,\text{s}$.
   * CortexDB also triggers an immediate sync on tab switches (`visibilitychange` / `pagehide`) or whenever you click **Save Now** (*Jetzt sichern*).
2. **Portable Snapshots (`JSON Export` / `JSON Import`):**
   * Click **JSON Export** to download your entire database (including synaptic weights) as a portable `.json` archive, and restore it anytime via **JSON Import**.
3. **Volatile Sandbox Mode & `Zero-Wipe`:**
   * Unchecking **Local Persistence (`IndexedDB`)** immediately purges browser storage and switches into **Volatile Sandbox-RAM** mode for confidential sessions.
   * Clicking **Zero-Wipe** in the top-right header overwrites all `TypedArrays`, BM25+ postings, the $64\text{-byte}$ `IsolatedBridge` buffer, and `IndexedDB` stores deterministically with `0x00` bytes.

---

## 4. Developer Tutorial: The AdaMind Language (.adm) & Python Runtime

Alongside the browser database, the repository includes the formal **AdaMind** (`.adm`) language specification and open-source reference implementations in Python and Rust (`adamind-opensource-v0.1.0.zip`).

### Neurobiological Mathematics & Hybrid Retrieval Formulas

1. **Variational Free Energy ($F$) & Split-Channel Prediction Error:**
   Each cortical column minimizes precision-weighted prediction error between bottom-up sensory input $S$ and top-down generative prior $P$:

   $$
   E_{\text{on}} = S \setminus P, \qquad E_{\text{off}} = P \setminus S, \qquad \varepsilon = \frac{\vert E_{\text{on}}\vert + \vert E_{\text{off}}\vert}{\vert S\vert + \vert P\vert}
   $$

   $$
   F = \varepsilon \cdot \Pi_{\text{ACh}} \quad \text{where} \quad \Pi_{\text{ACh}} = 0.5 + C_{\text{ACh}}
   $$

2. **Dopaminergic Temporal-Difference Reward Prediction Error ($\delta_t$):**

   $$
   \delta_t = R_{\text{obs}} + \gamma V(s_{t+1}) - V(s_t), \qquad \gamma = 0.95
   $$

3. **Hybrid Neuro-RAG Scoring Formula in CortexDB:**
   For every candidate chunk $c$, CortexDB combines normalized BM25+ ($k_1 = 1.5, b = 0.75, \delta = 1.0$), $2048\text{-bit}$ SDR overlap, exact phrase/heading boost $\beta_{\text{phrase}}$, and long-term synaptic weight $w_{\text{LTP}}(c)$:

   $$
   \text{Score}(q, c) = \left( 0.56 \cdot \widehat{\text{BM25}^+}(q, c) + 0.34 \cdot \frac{\vert q_{\text{SDR}} \cap c_{\text{SDR}}\vert}{\vert q_{\text{SDR}}\vert} + \min(0.28, \beta_{\text{phrase}}) \right) \cdot \left(0.92 + 0.08 \cdot w_{\text{LTP}}(c)\right)
   $$

### Designing a Custom AdaMind Module

Instead of imperative loops, an `.adm` module declares canonical cortical laminae (`lamina I` through `lamina VI`), homeostatic safety bounds, and subcortical gates:

```text
// Example: Custom associative cortical module in AdaMind (custom_column.adm)
module CustomKnowledgeCortex {

    column SemanticIntegrator(dim: 2048, sparsity: 0.02) {
        state internal_belief: SDR<2048, 0.02>;

        // Layer 3: Protection against epileptiform runaway excitation (> 15% active bits)
        homeostasis {
            target_firing_rate: 0.02;
            depolarization_block: 0.15;
            synaptic_scaling: true;
        }

        // Lamina IV: Split On/Off prediction error channels
        lamina IV(sensory_sdr: SDR<2048, 0.02>, sensory_gain: Float) {
            let on_error  = sensory_gain * (sensory_sdr - lamina_VI.prior);
            let off_error = sensory_gain * (lamina_VI.prior - sensory_sdr);
            emit on_error  -> lamina_II_III;
            emit off_error -> lamina_II_III;
        }

        // Lamina II/III: GABAergic k-Winner-Take-All lateral inhibition (k = 41)
        lamina II_III(on_error: SDR<2048, 0.02>, off_error: SDR<2048, 0.02>) {
            let residual = kwta_inhibit(merge(on_error, off_error), k: 41);
            emit residual -> lamina_V;
        }

        // Lamina V: Deep corticostriatal projection to Basal Ganglia (D1 Go / D2 NoGo / STN)
        lamina V(residual: SDR<2048, 0.02>) {
            internal_belief = kwta_inhibit(merge(internal_belief, residual), k: 41);
            emit internal_belief -> BasalGanglia;
        }
    }
}
```

### Running the Python Reference Runtime & IsolatedBridge v1.1

The Python reference runtime requires `Python >= 3.10` and `numpy`:

```bash
pip install numpy
```

**1. Run the End-to-End CerebralEnclave Telemetry Simulation:**

```bash
python3 adamind_runtime.py
```

**2. Use SDR Encoding & the 64-Byte Binary Wire Protocol in Your Own Python Code:**

```python
from adamind_runtime import (
    SDR,
    AdaMindRuntime,
    SharedMemoryRingBridge,
    BridgePacket,
    MessageType,
)

# 1. Initialize the cortical runtime & isolated shared-memory ring buffer
engine = AdaMindRuntime(dim=2048, sparsity=0.02)
bridge = SharedMemoryRingBridge(capacity_bytes=65536)

# 2. Deterministically project any symbol into a 2048-bit SDR (41 active bits)
stimulus = SDR.encode_symbol("cortical_plasticity", dim=2048, sparsity=0.02)

# 3. Transmit via 64-byte cache-aligned frame (Magic b"ADAM" + Dual CRC32)
bridge.send(BridgePacket(
    msg_type=MessageType.SDR_STREAM,
    seq_id=1,
    sdr=stimulus,
    valence=0.75,
))

incoming = bridge.receive()
result = engine.process_stimulus(incoming.sdr, label="plasticity", valence_hint=incoming.valence)

print(f"Free Energy: {result.initial_free_energy:.3f} -> {result.final_free_energy:.3f}")
print(f"Salience Gate: {result.relevance.value} | Action: {result.decision.action.value}")

# 4. Run two-stage sleep consolidation (NREM + REM) & zero-wipe shared memory
sleep_stats = engine.ltm.run_sleep_consolidation()
print(f"NREM Replays: {sleep_stats.nrem_replayed}, Arousal Drop: {sleep_stats.mean_arousal_reduction:.3f}")
bridge.close()
```

**3. Execute the Full Unit & Security Test Suite:**

```bash
unzip adamind-opensource-v0.1.0.zip
cd adamind-v0.1.0
python3 -m unittest discover -s tests -v
```

---

## 5. Frequently Asked Questions & Troubleshooting

* **Importing a PDF shows "No text layer found in this PDF":**
  The PDF consists solely of scanned page images without embedded character data. Run an OCR pass beforehand (e.g., `ocrmypdf input.pdf output.pdf`) and import the resulting file.
* **Copilot reports a network/CORS error in the browser:**
  The internal editor endpoint `api.githubcopilot.com` blocks direct browser cross-origin requests (`CORS`). Open **AI & API Keys -> GitHub / Copilot** and switch the endpoint profile to **`https://models.github.ai/inference/chat/completions`**, which natively supports browser CORS requests.
* **Do my imported documents stay saved after closing the browser?**
  Yes, provided you are not in Private/Incognito mode and **Local Persistence (`IndexedDB`)** is checked in the bottom-left panel. For long-term cross-device archiving, use **JSON Export**.
* **Can CortexDB operate completely offline?**
  Once loaded in the browser, `.txt`/`.md` ingestion, the entire $2048\text{-bit}$ SDR + BM25+ hybrid search engine, NREM/REM sleep consolidation, and the **Local AdaMind Neuro-Synthesizer** run $100\,\%$ offline in local RAM.

---

## 6. License & Contributing

This project is free and open-source software dual-licensed under **`MIT OR Apache-2.0`** at your option.

Contributions are welcome, particularly in the following areas:

1. **Cortical Hierarchies & Temporal Sequences:** Extending the SDR engine with multi-region temporal sequence memory (*L2/3 temporal pooling*).
2. **Web Worker Sharding:** Offloading the inverted $2048\text{-bit}$ index into dedicated Web Workers backed by `SharedArrayBuffer` for corpora exceeding $100,000+$ chunks.
3. **Native Compiler Backend:** Expanding the `adamind-isolated-bridge` Rust crate into a full `.adm` bytecode compiler.
