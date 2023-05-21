# Query by LLAMA

## Environment

- 安装 `torch`
- `pip install -r requirements.txt`
- 下载 `llama-7b`的模型；

## 构建llama.cpp的7B模型

- https://github.com/ggerganov/llama.cpp
  ```
  # obtain the original LLaMA model weights and place them in ./models
  ls ./models
  65B 30B 13B 7B tokenizer_checklist.chk tokenizer.model

  # install Python dependencies
  python3 -m pip install -r requirements.txt

  # convert the 7B model to ggml FP16 format
  python3 convert.py models/7B/

  # quantize the model to 4-bits (using q4_0 method)
  ./quantize ./models/7B/ggml-model-f16.bin ./models/7B/ggml-model-q4_0.bin q4_0

  # run the inference
  ./main -m ./models/7B/ggml-model-q4_0.bin -n 128
  ```
