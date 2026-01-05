# Multimodal Sequence Prediction with Bidirectional Temporal Encoding
**Author**: Tony-Okonta Ugochukwu
________________________________________
**Introduction**
This repository holds the final coursework for the Deep Neural Networks and Learning Systems (DNNLS) module.
The objective of this project is to analyze and improve a baseline multimodal storytelling model by modifying its temporal sequence encoder and evaluating the effect on text generation quality.
The baseline architecture was provided as part of the coursework and combines:

•	a visual autoencoder

•	a text autoencoder

•	a temporal recurrent model for sequence prediction

My work focuses on modifying the temporal sequence model and analysing its impact using established language generation metrics.
________________________________________
**Dataset**

The Dataset used for this project was hosted on huggingface:
•	https://huggingface.co/datasets/daniel3303/StoryReasoning
________________________________________
**Baseline Model**

The baseline model consists of:

•	a CNN-based visual autoencoder

•	an LSTM-based text autoencoder

•	a unidirectional GRU used as the temporal encoder

•	attention over the temporal hidden states

•	decoder modules for image and text prediction

The baseline was trained for 5 epochs, following the provided template.
________________________________________
**Proposed Modification**

**Bidirectional Temporal Encoder**

The main modification for this project was replacing the existing unidirectional GRU with a bidirectional GRU 

**Motivation**:

A bidirectional GRU can capture both past and future temporal context, which is beneficial for storytelling tasks where later events can provide context for earlier ones.

No changes were made to:

•	the dataset

•	the loss functions

•	the decoders

•	the training procedure

This ensures a fair comparison with the baseline model.
________________________________________
**Evaluation Metrics**
The model was evaluated with:

•	Cross-entropy loss (training loss)

•	BLEU score (text generation quality)

•	Perplexity (PPL) (language model confidence)

Metrics are reported for both training and validation splits.
________________________________________
**Results**

All figures and tables are provided in the results/ folder.

**Quantitative Results**

I compared the Existing baseline sequence model with the proposed bidirectional GRU architecture using training loss, BLEU-4 and perplexity 

•	The bidirectional model consistently achieves lower training loss compared to the baseline.

•	BLEU-4 scores improve, indicating better alignment between generated and reference narratives.

•	Perplexity increases slightly, suggesting reduced token-level confidence during generation.

This behaviour reflects a trade-off between global sequence coherence and local token certainty.
Figures showing training loss and BLEU/PPL comparisons can be found in the results/ folder.
________________________________________
**Interpretation**

Although perplexity increases, the improved BLEU scores indicate that the bidirectional model generates more coherent and contextually aligned stories. Since BLEU evaluates sequence-level similarity, this suggests that incorporating future context improves narrative structure, even if the model becomes less confident at each individual decoding step.
This outcome is expected in bidirectional temporal encoders, which prioritise global temporal reasoning over strictly causal left-to-right prediction.
________________________________________
**Limitations**

•	Training was limited to 5 epochs due to computational constraints

•	Only a single loss function was used

•	Evaluation relies on automatic metrics without human judgement
________________________________________
**Future Work**

Potential improvements include:

•	training for more epochs

•	introducing explicit validation loss tracking

•	experimenting with Bi-LSTM instead of Bi-GRU

•	tuning hidden dimensions and attention parameters
