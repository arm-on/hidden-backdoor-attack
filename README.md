# hidden-trigger-backdoor-attack
An implementation of the hidden trigger backdoor attack introduced by Saha et al. 

Note: This repo's content is based on the main repo of the paper which can be found here: https://github.com/UMBCvision/Hidden-Trigger-Backdoor-Attacks

## about the files and variables (the original version)

├── data_root
│   ├── train
│   ├── val
│   ├── test


- `data_root`: This is actually a string variable in the code showing the folder containing the real images of the ImageNet dataset. 
    - It contains three folders: `train`, `val`, and `test`. 
    
    - Inside each folder, there are folders with names called `wnid`. The `wnid` is something like `n0123` and represents a class of objects. For instance, a unique `wnid` is associated with `chicken`, while another one represents `cat`. 

    - A string like `{data_root}/train/n0123/n0123_30.JPEG` is the path to a JPEG file of the class `n0123` which should be used for the `training` phase.

- `ImageNet_data_list`: A folder located in the root of the project containing some files showing the path to all images used for `training`, `testing`, and `finetuning`. 

    - It contains three folders: `poison_generation`, `test`, and `finetune`. 
    - Each of these folders contain files like `n0123.txt`.
    - Inside a file like `n0123.txt`, we find the path to a `JPEG` file at each line.
        - For instance: `n0123.txt` contains a line like `n0123/n0123_4291.JPEG`.

- `source_wnid_list.txt`: A file containing the source class IDs (remember, we wanted the images belonging to the `source` class to be classified as the ones belonging to the `target` class). 

    - We can consider multiple source classes (more than one class).
    - Each source class ID should be written in one line of this file (`source_wnid_list.txt`).
    - Therefore, this file contains lines like this:
        - `n0123`
        - `n0234`
        - `n0345`
