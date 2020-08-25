# gluon_bLNet
Proposed in **Big-Little Net: An Efficient Multi-Scale Feature Representation for Visual and Speech Recognition** is a novel architecture for learning multi-scale feature representations with good tradeoffs between speed and accuracy. Implementation on bLNet is based on [official repo](https://github.com/IBM/BigLittleNet).


### FP16 Training

telsa v100 (16G) * 8

```
python train.py --rec-train /home/ubuntu/data/train.rec --rec-train-idx /home/ubuntu/data/train.idx --rec-val /home/ubuntu/data/val.rec --rec-val-idx /home/ubuntu/data/val.idx  --model blresnet50_v1 --mode hybrid  --lr 0.9 --lr-mode cosine --num-epochs 120 --batch-size 288 --num-gpus 8 -j 60 --warmup-epochs 5 --dtype float16 --use-rec --last-gamma --no-wd --label-smoothing --save-dir params_resnet50_v1_best --logging-file resnet50_v1_best.log
```

telsa v100 (16G) * 1

Speed: 74.567866 samples/sec

```
python train.py --rec-train /home/ubuntu/data/train.rec --rec-train-idx /home/ubuntu/data/train.idx --rec-val /home/ubuntu/data/val.rec --rec-val-idx /home/ubuntu/data/val.idx  --model blresnet50_v1 --mode hybrid  --lr 0.9 --lr-mode cosine --num-epochs 120 --batch-size 288 --num-gpus 1 -j 60 --warmup-epochs 5 --dtype float16 --use-rec --last-gamma --no-wd --label-smoothing --save-dir params_resnet50_v1_best --logging-file resnet50_v1_best.log
```



