# LLM to Reasoning Model 

# ✨ Quickstart Manual
### 📚 Installing Dependencies 
In this project we will be using unsloth, a library for finetuning LLMs with limited memory! 
- Install with pip (recommended) for Linux devices:
```bash
pip install unsloth
```
- Install with pip for Kaggle Notebook Users (option available for Mac)
```
!pip install unsloth vllm
```
- Install with pip for Colab Notebook Users (option available for Mac)
```
!pip install --no-deps unsloth vllm
```
### 📚 Uploading Training & Test Datasets
- **Synthetic GSM8K:** Using the [synthetic GSM8K from Hugging Face]([url](https://huggingface.co/datasets/gretelai/gsm8k-synthetic-diverse-8b))
  - Downloading the synthetic GSM8K requires a Hugging Face Token
  - Uploading on Kaggle...
    ```
    from huggingface_hub import login
    import os
    # Read token from Kaggle environment variable
    hf_token = os.environ.get("HF_TOKEN")
    login(token=hf_token)
    ```
  - Uploading on Google Colab...
    ```
    from huggingface_hub import login
    from google.colab import auth
    # Authentication for Hugging Face & Colab
    auth.authenticate_user()
    login(token='HF token') # You'll need to replace this with your own token!
    ```
- **Real GSM8K:** The real GSM8K can be downloaded from OpenAI
  ```
  # Training data 
  def load_real_gsm8k(split="train") -> Dataset:
      return load_dataset('openai/gsm8k', 'main')[split]
  ```
### 📚 Guide to this Repo
1. CoT (1).ipynb - contains the accuracy test on GSM8K Data (Test sample: 1319 examples) using simple CoT style prompting.
2. ToT Accuracy.pdf - contains the accuracy test on GSM8K Data (Test sample: 1319 examples) using ToT style prompting. We had an error saving the results and needed to upload pdf to include the outputs.
3. ToT.ipynb - the notebook and accuracy test ran on 10 examples from GSM8k test.
4. grpo-on-synthetic-data.ipynb - contains the test of accuracy on synthetic vs real data.
5. Unsloth training_Qwen2_5_(3B)_GRPO.ipynb - training the reasoning model using GSM8K, QWEN2.5 (3B parameters), and GRPO to save the parameters "grpo_saved_lora" used in other notebooks.
