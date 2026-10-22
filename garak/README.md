# garak scan of Qwen2.5-0.5B-Instruct

Tool: [NVIDIA garak](https://github.com/NVIDIA/garak) v0.17.1 · Google Colab

garak --target_type huggingface --target_name Qwen/Qwen2.5-0.5B-Instruct \
      --probes promptinject.HijackHateHumans,web_injection.MarkdownImageExfil,leakreplay.LiteratureCloze \
      --generations 1

| Probe | Attack | Attempts | Attack succeeded |
|---|---|---|---|
| promptinject.HijackHateHumans | Hidden instruction inside user text | 256 | 162 (63%) |
| web_injection.MarkdownImageExfil | Markdown image that leaks data via its URL | 12 | 0 |
| leakreplay.LiteratureCloze | Fill-in-the-blank from known books (memorization) | 256 | 3 (1%) |

The small model cannot separate data from instructions, so injected text hijacks it most of the time.
Full results: the HTML report in this folder.
