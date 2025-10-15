
## Setup

1. You need approximately **80-90GB** VRAM. You can modify your GPU settings in `./config/config1.yaml`.
2. Set up your api key in `./config/config2.yaml`. If your rate per minute is less than 1000, we suggest lowering the
3. Download [dataset](https://github.com/yinjjiew/Data/raw/main/scoreflow_data/data.zip) and unzip it in this directory `./`.
4. To set up the environment, follow these steps:

```bash
conda create -n scoreflow python=3.10
source activate scoreflow
# Install MetaGPT locally to resolve any conflicts
unzip metagpt_local.zip
cd metagpt_local
pip install .
cd ..
pip install -r requirements.txt
```
You can ignore the dependency error of metagpt 1.0.0.


## Generate Workflow Graph and Get Scores (For Large Model)
Modify Generator API in generator_large.py, then run

```bash
bash run_pipeline_large.sh <DATASET> <TASK> <EPOCH>
bash run_pipeline_large.sh GSM8K optimize 0
```

<!-- 
## Optimization Process

To optimize the model, follow these steps iteratively from `i = 0` then `i = 1`, and so on:

```bash
python generate.py --dataset=HumanEval --task=optimize --epoch=i
python evaluate.py --dataset=HumanEval --task=optimize --epoch=i
accelerate launch --num_processes=1 optimize.py --epoch=i
```

You can change the number of iterations by incrementing `i`. The dataset you can choose: HumanEval, MBPP, MATH, GSM8K, DROP, and HotpotQA.

## Inference

To run inference on the test set, execute:

```bash
python generate.py --dataset=HumanEval --task=inference --epoch=2
python evaluate.py --dataset=HumanEval --task=inference --epoch=2
```

## Notes

- Adjust the number of epochs as needed.
- Ensure all dependencies are installed from `requirements.txt`.
- The optimization and inference scripts should be run sequentially.
- If `evaluate.py` gets stuck, try rerunning it.
- We have added the majority-optimal workflow structure for different tasks in this link: [examples](https://github.com/yinjjiew/Data/raw/main/scoreflow_data/examples.zip).

## Citation
```
@article{wang2025scoreflow,
  title={ScoreFlow: Mastering LLM Agent Workflows via Score-based Preference Optimization},
  author={Wang, Yinjie and Yang, Ling and Li, Guohao and Wang, Mengdi and Aragam, Bryon},
  journal={arXiv preprint arXiv:2502.04306},
  year={2025}
}
``` -->
