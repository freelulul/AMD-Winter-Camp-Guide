### Pre-install

```she
# Login
Use SSH with the given username and 2FA key to login HACC@NUS
ssh username@xacchead.d2.comp.nus.edu.sg

# Interactive access commands for nodes
srun -p mi210_u280_u55c --cpus-per-task=64 --pty bash -i
                                        32
                                        16
                                         8
                                         4 

```

### Install

```she
git clone https://github.com/ultralytics/yolov5  # clone
cd yolov5
pip install -r requirements.txt  # install

# Using local dataset COCO on /local_data/coco
Change yolov5/train.py line 171:
train_path, val_path = data_dict["train"], data_dict["val"]
to 
train_path, val_path = "/local_data/coco/images/train2017", "/local_data/coco/images/val2017"
```

### Training

```she
# Single GPU training
python train.py --data coco.yaml --epochs 100 --weights '' --cfg yolov5n.yaml  --batch-size 128
                                                                 yolov5s                    64
                                                                 yolov5m                    40
                                                                 yolov5l                    24
                                                                 yolov5x                    16
# Multi-GPU training
# Two
python -m torch.distributed.run --nproc_per_node 2 train.py --batch 128 --data coco.yaml --weights yolov5s.pt --device 0,1

# Four
python -m torch.distributed.run --nproc_per_node 4 train.py --batch 128 --data coco.yaml --weights yolov5s.pt --device 0,1,2,3
```

