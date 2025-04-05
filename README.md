🔐 SELinux Policy Enhancement via Deep Learning-Based AVC Log Analysis

This project presents an AI-driven framework to analyze SELinux AVC logs from Android devices and identify malicious behavior. Using deep learning models like BiLSTM, GRU, and BiLSTM with attention, the system classifies log sequences as benign or malicious, and aids in dynamic SELinux policy adjustments.

📌 Project Objectives

Automate the classification of AVC (Access Vector Cache) logs as malicious or benign

Leverage sequence modeling to detect attack patterns across multiple log entries

Provide interpretability using attention mechanisms to guide SELinux policy tuning

Mitigate potential vulnerabilities through dynamic policy feedback

📚 Background

Android uses Security-Enhanced Linux (SELinux) for Mandatory Access Control (MAC). Every access attempt not explicitly permitted by the SELinux policy is denied and logged as an AVC message. However, distinguishing malicious AVC sequences from benign denials is extremely challenging due to the volume and complexity of logs.

🧠 Models Used

Bidirectional LSTM

Bidirectional GRU

BiLSTM + Attention Layer

All models take 10-time-step sequences (from PCA-reduced AVC logs) as input and output a binary classification (Malicious/Benign).

🛠️ Methodology

🔍 Data Collection

Logs collected from Android Emulator using:

adb logcat (filtered with grep avc:)

monkey command for automated UI interactions

Two labeled datasets:

Benign logs from normal app activity

Malicious logs from simulated attacks

🧹 Preprocessing & Feature Engineering

Extracted fields: Timestamp, SContext, TContext, Permissions, etc.

Encoded and normalized features

Applied PCA for dimensionality reduction (top 5 components)

Generated fixed-size sequences (10 time steps)

🧠 Deep Learning Pipeline

Sequence classification using BiLSTM/GRU models

Attention layer in BiLSTM+Attention model for interpretability

High performance (~89% validation accuracy)

🔥 Attention Insights

The attention layer highlights specific log events that influenced the classification, helping:

Identify policy violations linked to attacks

Recommend precise SELinux policy changes

Reduce false positives by clarifying benign patterns

📈 Results

Model

Train Accuracy

Validation Accuracy

BiLSTM

90.32%

88.72%

BiGRU

89.64%

88.80%

BiLSTM + Attention

89.95%

89.10%

🛡️ Policy Adjustment Strategy

Using attention-weighted AVC logs:

Suggest allow rules for benign-but-blocked behavior

Reinforce deny rules for attack-like access attempts

Improve SELinux security without breaking app functionality

📦 Project Structure

