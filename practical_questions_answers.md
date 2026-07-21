# Workshop 2 — Practical Questions & Answers

## RNN vs LSTM Comparison on IMDB Sentiment Classification

| Question | What to look at | Your finding |
|----------|----------------|--------------|
| **RQ1** | Accuracy — Best val accuracy of each model | **LSTM wins**: LSTM best val accuracy = **0.538** vs. Simple RNN best val accuracy = **0.526** |
| **RQ2** | Cost — Training time of each model | **LSTM is ~2× faster**: LSTM trained in **112.4 s** vs. Simple RNN in **215.9 s** |
| **RQ3** | Long-sequence effect — Accuracy-by-length table (Step 8.8) | **LSTM handles long reviews much better**: on long reviews (>200 words, 166 samples) LSTM achieves **0.590** accuracy vs. Simple RNN's **0.506** (near random chance) |
| **RQ4** | Recommendation — Weigh accuracy vs. speed for the team | **Use LSTM.** It is superior on every axis — higher accuracy (+1.2 pp overall, +8.4 pp on long reviews), nearly half the training time, and far better at retaining context over long sequences. There is no trade-off here; LSTM dominates Simple RNN on both quality and cost for this IMDB sentiment task. |


The Simple RNN struggles with the vanishing-gradient problem. its accuracy on long reviews (0.506) is essentially coin-flip, meaning it fails to propagate useful signal over 200+ tokens. LSTM's gating mechanism (forget/input/output gates) directly addresses this, which is why it excels on longer sequences and converges faster overall.
