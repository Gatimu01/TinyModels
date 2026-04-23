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


### Direction for My Project

* Focus on **efficient small-scale models under compute constraints**
* Explore:

  * Positional encoding choices (RoPE vs sinusoidal)
  * Model size vs performance tradeoffs
  * Training efficiency (fewer steps, less compute)

---

*Scaling Laws for Neural Language Models*

Inductive Inference:
The process of learning general patterns from specific training data and applying them to unseen examples.

Inductive Bias:
The assumptions a model uses to guide learning and generalization.
Big models rely on scale while Small models rely on good inductive bias

Power Laws:
- A relationship where performance scales as a power of model size, data, or compute
- Typically of the form y ∝ x^a, where a is a small exponent
- Leads to predictable improvements with diminishing returns
- Enables forecasting performance as models scale
  
Scaling Laws Insight:
- Language model performance (cross-entropy loss) improves predictably as model size, data, and compute increase
- Improvements follow a power-law relationship
- Efficient training requires balancing model size and data, not maximizing one alone
- Larger models learn faster per sample (higher sample efficiency)
- Training to full convergence is compute-inefficient
- Optimal strategy: train larger models for fewer steps and stop early
- Language is a universal interface for many reasoning tasks
- Large amounts of text data enable scalable self-supervised learning
- This combination makes language modeling ideal for studying AI systems
- Architecture influences parameter count
- However, for a fixed parameter budget, performance is relatively insensitive to model shape (depth vs width)
- Scaling (N, D, C) dominates performance improvements
- Performance improves predictably with scale, following a power-law, as long as model size(N), data(D), and compute(C) are balanced.
- Good performance is not about more data or bigger models—it’s about balancing them correctly. 8x improvement on model size= 5x improvement on datasize
- Larger models require proportionally less data increase due to higher sample efficiency
- Early training behavior can be used to estimate long-term performance as the curve is always the same for large and small models. Train for 1000 steps you can predict the performance for 10000 steps
- Enables early stopping and efficient use of compute
- Performance on new data distributions is strongly correlated with validation performanc. if Loss=L the in the new distribution Loss= L + constant (Performs badly initially the improves to what the training trend loss looked like)
- Improvements in training/validation performance translate directly to improvements in transfer. Models are really capable of generalizing.
- Larger models learn patterns more quickly due to higher capacity and They require fewer training steps and less data to reach the same performance level
- Smaller models need more data and longer training to achieve similar results
- Scaling Insight (Convergence):
- Training to full convergence is compute-inefficient
- Larger models trained for fewer steps achieve better performance under a fixed compute budget
- Optimal training allocates compute to early learning rather than late-stage convergence (Because performance dwindles and its compute expensize....Cost > than benefit)
- Optimal batch size depends on gradient noise scale and increases during training
- Larger batches improve training efficiency but require proper learning rate scaling
- Instability arises from mismatch between batch size and learning rate, not batch size alone

Intrinsic Dimensionality:
- The minimum number of variables needed to describe the data
- Real-world data often lies on a lower-dimensional manifold within a high-dimensional space
- In language, structure (syntax, semantics) reduces intrinsic dimensionality
- Models aim to learn this underlying structure efficiently

### Research Questions Emerging
_*Attention is all you need
_* How can we reduce the **quadratic complexity** while preserving performance?
* Can **smaller models** achieve similar behavior with better training strategies?
* Can architectural changes (e.g., RoPE, alternative sequence models) improve efficiency?
_* Scaling laws_
- Do architectural choices matter more in small models than in large-scale regimes?

---


* Start implementing:

  * Tiny Transformer baseline
  * Compare positional encodings (RoPE vs sinusoidal)
