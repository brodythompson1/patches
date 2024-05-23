# Data Preparation

Note that Many of the Instructions below come from the original VideoMAE Paper. The model is trained in the same way with our tweaks being made to the number of patches.

We  unsuccessfully pre-trained and fine-tuned PATCHES. We attempted to use [Kinetics400](https://deepmind.com/research/open-source/kinetics)

- The pre-processing of **Kinetics400** can be summarized into 3 steps:

  1. Download the dataset from [official website](https://deepmind.com/research/open-source/kinetics).

  2. Preprocess the dataset by resizing the short edge of video to **320px**. You can refer to [MMAction2 Data Benchmark](https://github.com/open-mmlab/mmaction2) for [TSN](https://github.com/open-mmlab/mmaction2/tree/master/configs/recognition/tsn#kinetics-400-data-benchmark-8-gpus-resnet50-imagenet-pretrain-3-segments) and [SlowOnly](https://github.com/open-mmlab/mmaction2/tree/master/configs/recognition/slowonly#kinetics-400-data-benchmark). <br>
**Recommend**: [OpenDataLab](https://opendatalab.com/) provides a copy of [Kinetics400](https://opendatalab.com/Kinetics-400) dataset, you can download Kinetics dataset with **short edge 320px** from [here](https://opendatalab.com/Kinetics-400).<br>

  3. Generate annotations needed for dataloader ("<path_to_video> <video_class>" in annotations). The annotation usually includes `train.csv`, `val.csv` and `test.csv` ( here `test.csv` is the same as `val.csv`). The format of `*.csv` file is like:

     ```
     dataset_root/video_1.mp4  label_1
     dataset_root/video_2.mp4  label_2
     dataset_root/video_3.mp4  label_3
     ...
     dataset_root/video_N.mp4  label_N
     ```

