## Lightweight Fine-Tuning of Foundation Model with PEFT (Parameter Efficient Fine-Tuning)

### Overview

This notebook demonstrates how to perform lightweight fine-tuning of a pre-trained NLP model using PEFT (Parameter Efficient Fine-Tuning). The notebook is divided into two main parts:
1. **Base Model Evaluation**
2. **PEFT Fine-Tuning**

### Base Model Evaluation

1. **Loading and Preparing the Dataset:**
   - The notebook starts by loading a dataset and preparing it for training. The dataset is tokenized using a tokenizer compatible with the pre-trained model. In our case: `distilbert-base-uncased-finetuned-sst-2-english`

2. **Loading the Pre-trained Model:**
   - A pre-trained model is loaded from the Hugging Face model hub. The model's parameters are then frozen to prevent them from being updated during training. This helps to retain the learned features from the large corpus on which the model was originally trained.

3. **Evaluating the untrained model:**
   - Evaluated the untrained model according to the project rubric with `trainer.evaluate()`

### PEFT Fine-Tuning

1. **PEFT Configuration:**
   - The notebook then configures the PEFT approach by defining a lightweight adapter module (e.g., LoRA - Low-Rank Adaptation) that will be fine-tuned. This involves setting up a configuration for the adapter.

2. **Integrating the Adapter:**
   - The adapter module is integrated into the pre-trained model. This allows for fine-tuning only a small number of additional parameters, making the process more efficient. In our case, target modules are: `["q_lin", "k_lin", "v_lin"]`

3. **Fine-Tuning with PEFT:**
   - The model, now equipped with the adapter, undergoes further fine-tuning on the same dataset. This step focuses on adjusting the adapter parameters while keeping the majority of the model parameters frozen.

4. **Evaluating the Model:**
   - Finally, the notebook evaluates the performance of the fine-tuned model on a test set, comparing its performance to ensure that the lightweight fine-tuning has been effective.

### Evaluation Accuracy Comparison

| Method                | Test Evaluation Accuracy |
|-----------------------|--------------------------|
| Before Training       | 0.168125                 |
| PEFT Fine-Tuning      | 0.705625                 |

**The saved PEFT LoRA model is loaded, and inference is performed on a custom text in the final section.**

### Summary

For detailed code and step-by-step execution, refer to the cells in the notebook. Each section is well-commented to provide additional context.