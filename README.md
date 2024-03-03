# hidden-trigger-backdoor-attack
An implementation of the hidden trigger backdoor attack introduced by Saha et al. 

Note: This repo's content is based on the main repo of the paper which can be found here: https://github.com/UMBCvision/Hidden-Trigger-Backdoor-Attacks

## about the files and variables (the original version)

- `data_root`: the folder containing the real images of the ImageNet dataset. It contains three folders: `train`, `val`, and `test`. Inside each folder, there are folders with names called `wnid`. The `wnid` is something like `n0123` and represents a class of objects. For instance, a unique `wnid` is associated with `chicken`, while another one represents `cat`. 

    - A string like `{data_root}/train/n0123/n0123_30.JPEG` is the path to a JPEG file of the class `n0123` which should be used for the `training` phase.