* Repo for the Clairaudience model
* Install with https://haoxiangsnr.github.io/spiking-fullsubnet/getting_started/installation.html

## Running Inference
```bash
cd /root/code/spiking-fullsubnet/recipes/intel_ndns/spike_fsb

conda activate spiking-fullsubnet

python run.py -C baseline_s.toml -M test --ckpt_path /root/code/spiking-fullsubnet/recipes/intel_ndns/spike_fsb/exp/checkpoints/best
```

## Changes to the Config 
* Line 63 cumulative laplace norm changed to offline laplace norm 
```toml
norm_type = "offline_laplace_norm"
```

## How Inference Works
* Gets the trainer path from `baseline_s.toml`, yielding `trainer.Trainer`.
* Passes the test_dataloader to `trainer.test`.
* 