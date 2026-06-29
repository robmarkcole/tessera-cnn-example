See https://toao.com/blog/earth-observation-budget-solar-farms-tiny-model for an explanation of this codebase

This project uses [uv](https://github.com/astral-sh/uv)

## Running this project

First you will want to download the OSM solar farm UK data and prepare the tiles:

```
sudo apt update             
sudo apt install gdal-bin libgdal-dev python3-gdal -y

uv run prepare.py --download
```

then training (assumes a GPU)

```
uv run train.py

Training for up to 50 epochs...
Epoch   1/50 | Train Loss: 0.6848, IoU: 0.3768 | Val Loss: 0.6516, IoU: 0.5734                                                                                                     
  -> Saved best model (IoU: 0.5734)
Epoch   2/50 | Train Loss: 0.5934, IoU: 0.6589 | Val Loss: 0.5917, IoU: 0.6131                                                                                                     
  -> Saved best model (IoU: 0.6131)
Epoch   3/50 | Train Loss: 0.5254, IoU: 0.6807 | Val Loss: 0.5712, IoU: 0.5279                                                                                                     
Epoch   4/50 | Train Loss: 0.4726, IoU: 0.6624 | Val Loss: 0.5460, IoU: 0.6373                                                                                                     
  -> Saved best model (IoU: 0.6373)
Epoch   5/50 | Train Loss: 0.4253, IoU: 0.7023 | Val Loss: 0.5634, IoU: 0.6352                                                                                                     
Epoch   6/50 | Train Loss: 0.4073, IoU: 0.7112 | Val Loss: 0.5633, IoU: 0.6458                                                                                                     
  -> Saved best model (IoU: 0.6458)
Epoch   7/50 | Train Loss: 0.4011, IoU: 0.7156 | Val Loss: 0.5698, IoU: 0.6559                                                                                                     
  -> Saved best model (IoU: 0.6559)
Epoch   8/50 | Train Loss: 0.4036, IoU: 0.7164 | Val Loss: 0.5727, IoU: 0.6541                                                                                                     
Epoch   9/50 | Train Loss: 0.4023, IoU: 0.7276 | Val Loss: 0.5730, IoU: 0.6403                                                                                                     
Epoch  10/50 | Train Loss: 0.3998, IoU: 0.7201 | Val Loss: 0.5812, IoU: 0.6507                                                                                                     
Epoch  11/50 | Train Loss: 0.4022, IoU: 0.7186 | Val Loss: 0.5723, IoU: 0.6526                                                                                                     
Epoch  12/50 | Train Loss: 0.3982, IoU: 0.7216 | Val Loss: 0.5764, IoU: 0.6433                                                                                                     
Epoch  13/50 | Train Loss: 0.3994, IoU: 0.7238 | Val Loss: 0.5627, IoU: 0.6545                                                                                                     
Epoch  14/50 | Train Loss: 0.3984, IoU: 0.7278 | Val Loss: 0.5757, IoU: 0.6468                                                                                                     
Epoch  15/50 | Train Loss: 0.3988, IoU: 0.7316 | Val Loss: 0.5753, IoU: 0.6266                                                                                                     
Epoch  16/50 | Train Loss: 0.3979, IoU: 0.7331 | Val Loss: 0.5771, IoU: 0.6560                                                                                                     
  -> Saved best model (IoU: 0.6560)
Epoch  17/50 | Train Loss: 0.3941, IoU: 0.7285 | Val Loss: 0.5687, IoU: 0.6621                                                                                                     
  -> Saved best model (IoU: 0.6621)
Epoch  18/50 | Train Loss: 0.4012, IoU: 0.7326 | Val Loss: 0.5750, IoU: 0.6386                                                                                                     
Epoch  19/50 | Train Loss: 0.3975, IoU: 0.7302 | Val Loss: 0.5729, IoU: 0.6542
Epoch  20/50 | Train Loss: 0.3950, IoU: 0.7447 | Val Loss: 0.5820, IoU: 0.6569
Epoch  21/50 | Train Loss: 0.3983, IoU: 0.7285 | Val Loss: 0.5787, IoU: 0.6481
Epoch  22/50 | Train Loss: 0.3988, IoU: 0.7255 | Val Loss: 0.5741, IoU: 0.6525
Epoch  23/50 | Train Loss: 0.3966, IoU: 0.7401 | Val Loss: 0.5758, IoU: 0.6399
Epoch  24/50 | Train Loss: 0.3936, IoU: 0.7448 | Val Loss: 0.5729, IoU: 0.6542
Epoch  25/50 | Train Loss: 0.3937, IoU: 0.7477 | Val Loss: 0.5762, IoU: 0.6470
Epoch  26/50 | Train Loss: 0.3912, IoU: 0.7458 | Val Loss: 0.5757, IoU: 0.6458
Epoch  27/50 | Train Loss: 0.3905, IoU: 0.7548 | Val Loss: 0.5767, IoU: 0.6497
Early stopping (no improvement for 10 epochs)

Training complete. Best IoU: 0.6621
Model saved to: models/solar_unet.pth

Saving validation predictions...
Saving predictions: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 292/292 [00:07<00:00, 36.76it/s]
Validation predictions saved to tmp/train_tifs/val_predictions/
wandb:
wandb: Run history:
wandb:         best_iou ▁▄▄▆▆▇█████████████████████
wandb:            epoch ▁▁▂▂▂▂▃▃▃▃▄▄▄▅▅▅▅▆▆▆▆▇▇▇▇██
wandb:    learning_rate ███████▇▇▇▇▆▆▆▆▅▅▅▄▄▃▃▃▂▂▁▁
wandb: patience_counter ▁▁▂▁▂▁▁▂▂▃▄▅▅▆▇▁▁▂▂▃▄▅▅▆▇▇█
wandb:       saved_best ██▁█▁██▁▁▁▁▁▁▁▁██▁▁▁▁▁▁▁▁▁▁
wandb:        train/iou ▁▆▇▆▇▇▇▇▇▇▇▇▇▇███████▇█████
wandb:       train/loss █▆▄▃▂▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁▁
wandb:          val/iou ▃▅▁▇▇▇██▇▇█▇█▇▆██▇██▇▇▇█▇▇▇
wandb:         val/loss █▄▃▁▂▂▃▃▃▃▃▃▂▃▃▃▃▃▃▃▃▃▃▃▃▃▃
wandb:    val/precision ▃▅▁▆▆▆▇▇▆▇▇▇▇▇█▇▇▇▇▇▇▇▇▇▇▇▇
wandb:               +1 ...
wandb:
wandb: Run summary:
wandb:         best_iou 0.66208
wandb:            epoch 27
wandb:    learning_rate 0.00047
wandb:       model_path models/solar_unet.pt...
wandb: patience_counter 10
wandb:       saved_best 0
wandb:        train/iou 0.75483
wandb:       train/loss 0.39054
wandb:          val/iou 0.64966
wandb:         val/loss 0.5767
wandb:               +2 ...
wandb:
wandb: 🚀 View run prime-river-1 at: https://wandb.ai/robmarkcole/geotessera-solarfarm/runs/8clik73a
wandb: _ÿ View project at: https://wandb.ai/robmarkcole/geotessera-solarfarm
wandb: Synced 6 W&B file(s), 0 media file(s), 0 artifact file(s) and 0 other file(s)
wandb: Find logs at: ./wandb/run-20260629_111415-8clik73a/logs
```

finally evaluate

```
uv run evaluate.py

Using device: cuda
Loading model from models/solar_unet.pth...
Model trained to epoch 16 with IoU 0.6621
Evaluating on 146 samples from patches/test
Evaluating: 100%|████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████████| 146/146 [00:05<00:00, 28.63it/s]

========================================
RESULTS
========================================
IoU:       0.6727
Dice:      0.8043
Precision: 0.7107
Recall:    0.9264
```
