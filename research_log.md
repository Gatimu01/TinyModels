## 📅 [2026-04-20] — Paper Study: Attention Is All You Need

### 📄 Paper

Attention Is All You Need
https://proceedings.neurips.cc/paper_files/paper/2017/file/3f5ee243547dee91fbd053c1c4a845aa-Paper.pdf

---

### Key Concepts Understood

* **Self-Attention**

  * Enables global interaction between all tokens in a sequence
  * Removes sequential dependency → allows full parallelization
  * Improves context understanding across long sequences

* **Multi-Head Attention**

  * Multiple attention heads learn different representations (syntax, semantics, dependencies)
  * Increases expressivity without requiring deeper networks

* **Positional Encoding**

  * Original paper uses **sinusoidal (absolute) encoding**
  * Explored alternatives:

    * RoPE (rotary positional encoding)
    * Relative positional encoding (RPE)
  * RoPE encodes position via rotation → captures relative relationships more naturally

---

### Why Self-Attention Works

* Fully parallelizable → efficient on GPUs
* No restriction to local context (unlike CNNs)
* Captures long-range dependencies effectively
* Dynamic weighting of token importance

---

### Limitations Identified

* **Quadratic complexity**: O(n²) with sequence length
* High memory and compute requirements
* Requires large datasets and training steps for strong performance
* Inefficient for long sequences compared to newer linear-time approaches

---

### Core Insights

* Performance gains in Transformers come primarily from **scaling (data + model size + compute)** rather than efficiency
* Attention provides flexibility but at a high computational cost
* There is a fundamental **efficiency vs performance tradeoff**

---

### Research Questions Emerging

* How can we reduce the **quadratic complexity** while preserving performance?
* Can **smaller models** achieve similar behavior with better training strategies?
* Can architectural changes (e.g., RoPE, alternative sequence models) improve efficiency?

---

### Direction for My Project

* Focus on **efficient small-scale models under compute constraints**
* Explore:

  * Positional encoding choices (RoPE vs sinusoidal)
  * Model size vs performance tradeoffs
  * Training efficiency (fewer steps, less compute)

---

### Next Steps

* Read: *Scaling Laws for Neural Language Models*
* Start implementing:

  * Tiny Transformer baseline
  * Compare positional encodings (RoPE vs sinusoidal)
