
## Small Models
### ShuffleNetV2 
```
python -m torch.distributed.launch --nproc_per_node=8 imagenet_mobile.py --cos -a shufflenetv2_1x --data /share1/classification_data/imagenet1k/ --epochs 300 --wd 4e-5 --gamma 0.1 -c checkpoints/imagenet/shufflenetv2_1x --train-batch 128 --opt-level O0
```


## Large Models
### SGE-ResNet
```
python -W ignore imagenet.py -a sge_resnet101 --data /share1/classification_data/imagenet1k/ --epochs 100 --schedule 30 60 90 --gamma 0.1 -c checkpoints/imagenet/sge_resnet101 --gpu-id 0,1,2,3,4,5,6,7
```
or faster
```
python -m torch.distributed.launch --nproc_per_node=8 imagenet_fast.py -a sge_resnet50 --data /share1/classification_data/imagenet1k/ --epochs 100 --schedule 30 60 90 --wd 1e-4 --gamma 0.1 -c checkpoints/imagenet/sge_resnet50 --train-batch 32 --opt-level O0 --wd-all --label-smoothing 0. --warmup 0
```
