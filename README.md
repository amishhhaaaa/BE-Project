# BE-Project

# Model 1 - Accuracy ~66
Frame encoder: a custom 4-stage CNN, trained from scratch. It takes 6 channels: the RGB frame plus the difference from the previous frame.  
Temporal model: a 2-layer Transformer encoder with a CLS token and learned position embeddings. It models how frames relate over time.  
Audio encoder: a small CNN on log-mel spectrograms.  
Fusion head: the video and audio embeddings are concatenated and passed through an MLP to give one AI-probability score.  

# Model 2 - Accuracy ~63-65
Type: A classical machine-learning classifier. It uses hand-built video features and scikit-learn’s Logistic Regression or Random Forest, whichever scores better. It has no neural network or pretrained model.  
Input: Frames are taken from 6 spots in each video and resized to 256×256. The model analyzes a pair of consecutive frames at each spot.  
Features: It computes 44 numbers per video: camera-noise level, sharpness, frequency spectrum, edge density, color saturation, motion (optical flow), frame flicker, and how much noise repeats between frames. Real cameras make fresh noise every frame, while AI video often doesn’t.  
Output and evaluation: It gives an AI-vs-real probability for each video. Accuracy is measured with 5-fold cross-validation (accuracy, AUC, confusion matrix), and the model is saved as ai_video_model_simple.pkl.  
