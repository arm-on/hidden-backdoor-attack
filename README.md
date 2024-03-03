# hidden-trigger-backdoor-attack
An implementation of the hidden trigger backdoor attack introduced by Saha et al. 

Note: This repo's content is based on the main repo of the paper which can be found here: https://github.com/UMBCvision/Hidden-Trigger-Backdoor-Attacks

## about the files and variables (the original version)

```
├── {data_root} variable, a.k.a. {clean_data_root} (the "data" folder)
│   ├── train
│   │   ├── n0123
│   │   │   ├── n0123_3451.JPEG
│   │   │   ├── n0123_6769.JPEG
│   │   │   ├── n0123_4341.JPEG
│   │   ├── n0234
│   │   ├── n0345
│   ├── val
│   ├── test
│   ├── triggers
│   │   ├── trigger_10.png
│   │   ├── trigger_11.png
│   │   ├── ...
│   │   ├── trigger_19.png
│   ├── {exp_ID} (will be created)
│   │   ├── multi_source_filelist.txt (WBC)
│   │   │   ├── LINE 1: n0123/n0123_3401.JPEG
│   │   │   ├── LINE 2: n0234/n0234_6941.JPEG
│   │   ├── finetune_filelist.txt (WBC)
│   │   ├── test_filelist.txt (WBC)
│   │   ├── patched_filelist.txt (WBC)
│   │   ├── poison_filelist.txt (WBC)

├── ImageNet_data_list
│   ├── finetune
│   │   ├── n0123.txt
│   │   │   ├── LINE 1: n0123/n0123_3401.JPEG
│   │   ├── n0234.txt
│   │   │   ├── LINE 1: n0234/n0234_6981.JPEG
│   ├── poison_generation
│   │   ├── n0345.txt
│   ├── test
│   │   ├── n0345.txt

├── patched_data/{exp_ID}/rand_loc_false/eps_16/patch_size_30/trigger_10/
│   │   ├── patched_data/arman/rand_loc_True/eps_16/patch_size_30/trigger_10/badnet_n03461385_37_epoch_0000054.png

├── poison_data/{exp_ID}/rand_loc_false/eps_16/patch_size_30/trigger_10/
│   │   ├── poison_data/arman/rand_loc_True/eps_16/patch_size_30/trigger_10/loss_03395_epoch_01_n02437312_2125_n03461385_36144_kk_00168.png
```

- `data_root`: This is actually a string variable in the code showing the folder containing the real images of the ImageNet dataset. 

    - In my case, the `data_root` was `/Users/armanmalekzadeh/Documents/GitHub/hidden-trigger-backdoor-attack/data`
    - It contains three folders: `train`, `val`, and `test`. 
    
    - Inside each folder, there are folders with names called `wnid`. The `wnid` is something like `n0123` and represents a class of objects. For instance, a unique `wnid` is associated with `chicken`, while another one represents `cat`. 

    - A string like `{data_root}/train/n0123/n0123_30.JPEG` is the path to a JPEG file of the class `n0123` which should be used for the `training` phase.

- `data/triggers`: A folder containing the triggers
    - Each trigger is a 80x80 RGB image formatted as `png`

- `data/{exp_ID}/multi_source_filelist.txt`: A file containing relative paths to the source class images. 
    - Each line of the file contains the relative path to an image belonging to a different source class.
        - For instance, the first line could be `n0123/n0123_3401.JPEG` while the second could be `n0234/n0234/6951.JPEG`.

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

