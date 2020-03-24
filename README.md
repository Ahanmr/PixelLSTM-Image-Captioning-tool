# PixelLSTM: Image Captioning tool for COCO Dataset


This repo contains code for:
Implementation and training of multi-task model which performs:
* image captioning
* sentence paraphrasing.


## Generate Data
In the data folder, you can find scripts for generating TF-records for mscoco dataset.

* To generate TF-records for MSCOCO
```
python -m data.coco_data_loader --num 10000
```

Args:
* `--num` : Number of images to be written in TF record. Do not specify this unless you want to generate a subset of entire dataset.

* Generate TF-records with Image, predicted caption and groundtruth caption
```

python -m data.coco_data_loader --precompute \
                                --record_path para_att_pred.tfrecord \
                                --feature_path coco_precomp/testall_ims.npy \
                                --captions_path <path_to_coco_captions>
```

* `feature_path`: This should be used if you have already extracted features for all the images. 
In this case, a sample in TF record would look like (Feature (1x2048 dim vector for an image), caption A, caption B) which are paraphrases.

## Training on COCO dataset

```
sh scripts/train_coco.sh
```

## Evaluation on COCO dataset

```
sh scripts/eval_coco.sh
```
