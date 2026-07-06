# Relatório de Trechos Removidos (Master vs diferencas)

Este relatório documenta os trechos de texto que estavam presentes na branch `master` mas foram **removidos** na branch atual (`diferencas`).

### Remoção em Bloco (Linha original: 307)
- **Localização:** `Seção: Challenges Encountered and Solutions Implemented > Subseção: Federated Learning Integration Scope`
- **Texto original removido do parágrafo:**
  > Flower is the framework used to coordinate federated training rounds: it sends model parameters to local clients, receives locally updated parameters, and aggregates them into a new global model

### Remoção em Bloco (Linha original: 320)
- **Localização:** `Seção: Results`
- **Texto original removido do parágrafo:**
  > \begin{longtable}{p{2.5cm} p{4.7cm} p{6.4cm}} \caption{Main technical terms used in the Results section.} \label{tab:technical_terms_results} \\ \toprule \textbf{Term} & \textbf{Meaning} & \textbf{Role in this project} \\ \midrule \endfirsthead \caption[]{Main technical terms used in the Results section

### Remoção em Bloco (Linha original: 410)
- **Localização:** `Seção: Results > Subseção: Mobile Application as Privacy Gateway`
- **Texto original removido do parágrafo:**
  > In the proposed workflow, a single ESP32 collects physiological signals from multiple wearable sensors

### Remoção em Bloco (Linha original: 614)
- **Localização:** `Seção: Results > Subseção: Model Architecture and Training Configuration > Subsubseção: Baseline and Proposed TabularMLP`
- **Texto original removido do parágrafo:**
  > Table~\ref{tab:model_architecture_comparison} summarizes the main architectural differences.

### Remoção em Bloco (Linha original: 622)
- **Localização:** `Seção: Results > Subseção: Model Architecture and Training Configuration > Subsubseção: Baseline and Proposed TabularMLP`
- **Texto original removido do parágrafo:**
  > \begin{longtable}{p{2.6cm} p{4.4cm} p{5.2cm}} \caption{Comparison between the baseline MLP and the proposed TabularMLP.} \label{tab:model_architecture_comparison}\\[-0.2em] \toprule \textbf{Aspect} & \textbf{Original baseline MLP} & \textbf{Proposed TabularMLP} \\ \midrule Hidden layers & Two fully connected layers. & Three fully connected layers with dimensions 128, 128, and 64. \\ \midrule Activation & ReLU. & GELU. \\ \midrule Normalization & Not used. & BatchNorm1d after each hidden linear layer. \\ \midrule Regularization & Limited. & Dropout with probability 0.25 and AdamW weight decay. \\ \midrule Output & Three class logits. & Three class logits. \\ \bottomrule \end{longtable}

### Remoção em Bloco (Linha original: 649)
- **Localização:** `Seção: Results > Subseção: Model Architecture and Training Configuration > Subsubseção: Training Strategy`
- **Texto original removido do parágrafo:**
  > \begin{table}[H] \centering \caption{Main training hyperparameters used in the TabularMLP experiments.} \label{tab:training_hyperparameters} \resizebox{\textwidth}{!}{% \begin{tabular}{lll} \toprule \textbf{Component} & \textbf{Value} & \textbf{Purpose} \\ \midrule Optimizer & AdamW & Adaptive optimization with decoupled weight regularization. \\ \midrule Learning rate & $2 \times 10^{-3}$ & Initial magnitude of parameter updates. \\ \midrule Weight decay & $10^{-3}$ & Penalizes overly large weights to reduce overfitting. \\ \midrule Batch size & 64 & Number of samples used per optimization step. \\ \midrule Maximum epochs & 300 & Upper bound on the number of training passes. \\ \midrule Learning-rate policy & Reduction after validation stagnation & Refines optimization when validation macro F1 stops improving. \\ \midrule Early stopping patience & 50 epochs & Stops training after prolonged lack of validation improvement. \\ \midrule Gradient clipping & 1.0 & Limits abrupt gradient updates. \\ \bottomrule \end{tabular}% } \end{table}

### Remoção em Bloco (Linha original: 700)
- **Localização:** `Seção: Results > Subseção: Experimental Classification Results`
- **Texto original removido do parágrafo:**
  > The configurations can be read as four experimental questions, summarized in Table~\ref{tab:experimental_questions}.

### Remoção em Bloco (Linha original: 702)
- **Localização:** `Seção: Results > Subseção: Experimental Classification Results`
- **Texto original removido do parágrafo:**
  > \begin{table}[H] \centering \caption{Experimental questions represented by the evaluated WESAD configurations.} \label{tab:experimental_questions} \resizebox{\textwidth}{!}{% \begin{tabular}{p{3.5cm} p{5.2cm} p{5.5cm}} \toprule \textbf{Configuration family} & \textbf{Question addressed} & \textbf{Reason for evaluation} \\ \midrule Original baseline & Is a simple MLP already sufficient for the extracted features? & Establishes a reproducible reference point. \\ \midrule New full & What is the best local validation performance with all features and standardization? & Measures the upper local-performance reference. \\ \midrule No demographics / no scaler & What is the cost of privacy-oriented and deployment-oriented constraints? & Removes quasi-identifiers and avoids scaler synchronization across services. \\ \midrule ESP-friendly & What is the cost of using features easier to compute in an embedded path? & Estimates feasibility for simplified sensor-side processing. \\ \bottomrule \end{tabular}% } \end{table}

### Remoção em Bloco (Linha original: 789)
- **Localização:** `Seção: Results > Subseção: Integration with Federated Learning`
- **Texto original removido do parágrafo:**
  > \begin{table}[H] \centering \caption{Main software contracts in the federated learning integration.} \label{tab:federated_contracts} \resizebox{\textwidth}{!}{% \begin{tabular}{p{3.2cm} p{4.5cm} p{6.0cm}} \toprule \textbf{Component} & \textbf{Input} & \textbf{Responsibility} \\ \midrule Local API & HMAC-authenticated physiological windows. & Validates requests and persists accepted records in PostgreSQL. \\ \midrule PostgreSQL & Accepted sensor windows. & Stores institutional physiological records locally. \\ \midrule Local Flower client & Local database records and global parameters. & Trains the TabularMLP locally and returns updated model parameters and metrics. \\ \midrule Global Flower server & Client model updates. & Coordinates federated rounds and aggregates parameters using FedAvg. \\ \midrule Global Model API & Exported global model artifact and metadata. & Publishes the latest ONNX model and metadata for mobile retrieval. \\ \bottomrule \end{tabular}% } \end{table}

### Remoção em Bloco (Linha original: 861)
- **Localização:** `Seção: Conclusion`
- **Texto original removido do parágrafo:**
  > This study investigated federated learning as a privacy-preserving approach to occupational stress analysis, combining a systematic literature review with a practical prototype spanning wearable sensing, mobile anonymized communication, local model training, and federated coordination

