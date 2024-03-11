* Repo for the Clairaudience model
* Install with https://haoxiangsnr.github.io/spiking-fullsubnet/getting_started/installation.html

## Running Inference
```bash
cd /root/code/spiking-fullsubnet

conda activate spiking-fullsubnet

python run.py -C baseline_s.toml -M test --ckpt_path /root/code/spiking-fullsubnet/recipes/intel_ndns/spike_fsb/exp/checkpoints/best
```