# BE-Project

# Model 1
Frame encoder: a custom 4-stage CNN, trained from scratch. It takes 6 channels: the RGB frame plus the difference from the previous frame.
Temporal model: a 2-layer Transformer encoder with a CLS token and learned position embeddings. It models how frames relate over time.
Audio encoder: a small CNN on log-mel spectrograms.
Fusion head: the video and audio embeddings are concatenated and passed through an MLP to give one AI-probability score.
