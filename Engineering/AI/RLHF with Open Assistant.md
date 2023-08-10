### Open Assistant
Open Assistant (abbreviated as OA) is a chat-based and open-source assistant. The vision of the project is to make a large language model that can run on a single high-end consumer GPU. With some modifications, Open Assistant should also be able to interface with other third-party applications easily as well as retrieve information from databases and the Internet.

### How OA works
Consists in three steps:
- Collect demonstration data and train a supervised policy.
- Collect comparison data and train a reward model
- Optimize a policy against the reward model using reinforcement learning (RL)
### Open Assistant RLHF flow
![](../../_assets/oa-rlhf-flow.png)

### Recommended cloud provider:
- https://redmond.ai/

### System requirements:
- 8xA100 80GB (224 vCPU 768gb ram) (recommended)
- depend on the selected base model

### Setup environment

```bash
mambaforge/bin/mamba install jupyterlab code-server jupyterhub jupyter-vscode-proxy jupyterlab-git python=3.10 pytorch pytorch-cuda=11.8 cuda=11.8 cuda-nvcc=11.8 ninja cxx-compiler==1.5.2 -c nvidia -c pytorch -y
```

### Setup repo
```bash
git clone https://github.com/LAION-AI/Open-Assistant.git  #commit id: 0d4adb5f1ad6c38a828370414a584dd485165dce
cd ./Open-Assistant
cd ./model
mkdir -p .cache
mkdir -p .saved_models
export DATA_PATH=$PWD/.cache
export MODEL_PATH=$PWD/.saved_models
cd model_training
pip install -e .. --no-build-isolation
python -m pip install ../../oasst-data/
export PYTHONPATH=$PYTHONPATH:../../oasst-shared
```

### SFT training
```bash
export BS=8
deepspeed --include=localhost:0,1,2,3,4,5,6,7 --master_port 61000 trainer_sft.py \
--config defaults <your dataset> <your model> \
--cache_dir $DATA_PATH --output_dir $MODEL_PATH/sft_model \
--per_device_eval_batch_size $BS --per_device_train_batch_size $BS \
--deepspeed
```

### RM training
```bash
cd model_training

python trainer_rm.py --configs defaults_rm oasst-rm-2.1-pythia-1.4b \
--cache_dir /home/ubuntu/OA/model/model_training/.cache \
--output_dir ./rm_model
```

### RL training

Install singularity
```bash
wget https://github.com/sylabs/singularity/releases/download/v3.11.4/singularity-ce_3.11.4-jammy_amd64.deb
sudo apt install uidmap
sudo dpkg -i singularity-ce_3.11.4-jammy_amd64.deb
```

Build tritonserver
```bash
singularity build --sandbox tritonserver-pyt.sif docker://nvcr.io/nvidia/tritonserver:22.08-pyt-python-py3
```

Process a trained RM model to use in a tritonserver
```bash
python to_triton.py --configs <your config> --triton_mode rm
python to_triton.py --configs <your config> --triton_mode sft
```

Runs the RM on a specified GPU
```bash
SINGULARITYENV_CUDA_VISIBLE_DEVICES=7 singularity run --nv --bind .triton_models/model_store_rm:/model_store tritonserver-pyt.sif tritonserver --model-repository=/model_store --http-port 8001 --grpc-port 8002 --metrics-port 8003
SINGULARITYENV_CUDA_VISIBLE_DEVICES=6 singularity run --nv --bind .triton_models/model_store_sft:/model_store tritonserver-pyt.sif tritonserver --model-repository=/model_store --http-port 8004 --grpc-port 8005 --metrics-port 8006
```

```bash
export TRITON_HOST_RM=localhost:8002/<RM_MODEL_NAME>
export TRITON_HOST_REF=localhost:8005/<REF_MODEL_NAME>


CUDA_VISIBLE_DEVICES=0,1,2,3,4,5 OMP_NUM_THREADS=1 accelerate launch --main_process_port 29501 --config_file configs/accelerate_config.yaml --num_processes 6 trainer_rl.py --configs defaults defaults_rlhf <your config> <your dataset>
```