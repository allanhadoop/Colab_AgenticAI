-------------------Google Colab
https://github.com/allanhadoop/Colab_AgenticAI
https://colab.research.google.com/


Google colab shared code from Ed - 
https://colab.research.google.com/drive/1DjcrYDZldAXKJ08x1uYIVCtItoLPk1Wr?usp=sharing
https://colab.research.google.com/drive/1aMaEw8A56xs0bRM4lu8z7ou18jqyybGm?usp=sharing
https://colab.research.google.com/drive/1WD6Y2N7ctQi1X9wa6rpkg8UfyA4iSVuz?usp=sharing
https://colab.research.google.com/drive/1hhR9Z-yiqjUe7pJjVQw4c74z_V3VchLy?usp=sharing
https://colab.research.google.com/drive/1KSMxOCprsl1QRpt_Rq0UqCAyMtPqDQYx?usp=sharing

Access llama 3.1 base model from Meta approval  - https://huggingface.co/meta-llama/Llama-3.1-8B
There are chat or instruct variant of the model too ("meta-llama/Meta-Llama-3.1-8B-Instruct") - So they are built to consider prompts and chat utility (apply_chat_template) to take inout from list of dictionary to convert to special tokens.

Similarly get access to Google Gemma model from - https://huggingface.co/google/gemma-3-270m-it

------------Other models 
PHI4 = "microsoft/Phi-4-mini-instruct"
DEEPSEEK = "deepseek-ai/DeepSeek-V3.1"
QWEN_CODER = "Qwen/Qwen2.5-Coder-7B-Instruct"

Follow below steps on Google Colab -- 
T4 GPU instance is free. 
Kernel menu >> Disconnect and delete runtime
Reload the colab from fresh and Edit menu >> Clear All Outputs
Connect to a new T4 using the button at the top right
Select "View resources" from the menu on the top right to confirm you have a GPU
Rerun the cells in the colab, from the top down, starting with the pip installs

--------------------------Hugging Face platform (huggingface.co) ------------------------
1. Models - over 2+ millions 
2. Dataset - over 500k+ 
3. Spaces - Apps builder
4. Code libraries - E.g. Pytorch Transformers
    a. Hub (Python library) - Find/download/upload models and datasets
    b. dataset - Load, process, split and prepare training data
    c. transformers - Use popular Transformer models such as BERT, Llama, T5
    d. peft (parameter efficient fine tuning) - Customize a model without retraining the whole model
    e. trl (transformer reenforcement library) - Train models using techniques such as reinforcement learning
    f. accelerate - Make training work efficiently across GPUs/CPUs

-----------------Two API Levels of Hugging Face --------------
1. Pipelines - Higher level APIs to carry out standard tasks (preconfigured and inference tasks)
    a. Sentiment analysis 
    b. Classifier 
    c. Named entity recoginition 
    d. Question answers
    e. Summarizing 
    f. Translation
2. Tokenizers and Models - Lower level APIs to provide the most power and control 

---------------------Pipelines ----------------------
The pipelines API in HuggingFace is only for use for inference - running a model that has already been trained.

https://huggingface.co/docs/transformers/main_classes/pipelines
https://huggingface.co/docs/diffusers/en/api/pipelines/overview

--------------------Tokenizer-----------------
1. Tokenizer translate text into chunk of words called Tokens and it is assigned to id called token ID
2. Tokenizer has a vocab (database of tokens and special tokens (for eg. start of prompt -- this will inform model that prompt started)) -- Check excercise under Tokenizer folder 

Quantization is a way of making an AI model smaller and faster by storing its numbers with less precision. Quantization = reducing the number of digits used to store the model's numbers, so the model needs less memory. E.g. 0.73849217 Instead of storing it with lots of precision, quantization might store an approximation: 0.74 You've lost a little precision, but you save memory.

BitsAndBytesConfig is basically a set of instructions you give Hugging Face for how you want to quantize a model. Its like a "compression settings" object for your AI model.

quant_config = BitsAndBytesConfig(
    load_in_4bit=True,
    bnb_4bit_quant_type="nf4",  # NF4 stands for NormalFloat 4-bit. In simple terms, it is a smart way of doing 4-bit quantization, especially designed for neural-network/LLM weights.
    bnb_4bit_compute_dtype="float16"
)