# vLLM Benchmark Scripts

## Prerequisites for Nvidia

a. install Miniforge

```bash
wget https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-Linux-x86_64.sh
bash Miniforge3-Linux-x86_64.sh
source ~/.bashrc
conda create -n vllm_0_6_6_pip python=3.12
```

b. install vLLM

```bash
conda activate vllm_0_6_6_pip
pip install vllm==0.6.6
```

## Benchmark Serving

a. download multi-modal dataset (to the working directory)

```bash 
export HF_ENDPOINT=https://hf-mirror.com
huggingface-cli download --token [your HF token] --resume-download lmms-lab/LLaVA-OneVision-Data --cache-dir /data/hf_models/
```

b. check the models.conf file, specify your model file path if it is not same as the default. 

c. check the input_and_output_cases.conf file to understand how to specify dataset and out for the bencmark

d. run test cases

```bash
Syntax: vllm_benchmark_serving_cli.sh [-m] [-c] [-n] [-e] [-h]
options:
m  model ids, default all listed in conf
c  input and output case ids, default all listed in conf
n  card numbers, default all listed in conf


for example
```bash
./vllm_benchmark_serving_cli.sh -m 1 -c 1
```

e. check benchmark result (e.g, througput, time to first token ,etc.) in the log file under the directory benchmark_log


## Notes for Benchmark Serving Qwen-VL-Chat
You may need to manully patch your vLLM for the Qwen-VL-Chat issue on VLLM issue https://github.com/vllm-project/vllm/pull/11980/files# OxM-Specific-Solutions
