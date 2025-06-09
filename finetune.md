## Finetune

1. We use the `accelerate` package from Hugging Face for multi-GPU training.
2. Run `accelerate config` to setup your run configuration. The default accelerate config is in the `configs` folder.
3. Please specify the path to your training files in the `configs/tangoflux_config.yaml`. Samples of `data/train.json` and `data/val.json` have been provided. Replace them with your own audio.
4. `configs/tangoflux_config.yaml` defines the training file paths and model hyperparameters.
5. To finetune from the huggingface checkpoint execute `finetune.sh` or the following:

```bash
CUDA_VISIBLE_DEVICES=0,1 accelerate launch --config_file='configs/accelerator_config.yaml' tangoflux/train.py   --checkpointing_steps="best" --save_every=5 --config='configs/tangoflux_config.yaml' --load_from_hf
```
