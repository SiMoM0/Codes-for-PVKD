# Changes performed to run PVKD on Pandaset

#### Requirements

Same as PVKD plus:
* json
* gzip
* numpy-quaternion
* pandas

### Usage

Run pvkd to get predictions:

    CUDA_VISIBLE_DEVICES=0 python -u test_cyl_panda_tta.py

Convert label to original format

    python remap_semantic_labels.py -p out_cyl/test -s test --inverse

### Dataloader

* pc_dataset.py
    * add packages json, gzip, quaternion
    * add label map from pandaset to kitti format
    * add Pandaset dataset class
    * add getPoses function
    * add absouteFilePathsLidar for point cloud
    * add absouteFilePathsLabel for labels

* semantickitti.yaml: changes model and dataset paths

* pandaset.yaml: model and dataset configuration file for Pandaset and paths to it

* panda-set.yaml: label configuration for Pandaset

* dataset_semantickitti.py: change np.int to np.int64

### Inference

* test_cyl_panda_tta.py: script to run pvkd on the whole pandaset dataset

### Other

* remap_semantic_labels.py: change output label format and save directory