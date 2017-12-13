# 为了可视化对一个新的网络计算每一个单元
caffenet-yos 网络已经包括了每一个单元的可视化,但并不是每一个单元都包括,(总大小至少为几GB，分配起来很麻烦).
对于任何网络都可以通过计算来获得每一个单元的可视化:

* 要通过正则化优化找到导致高激活的合成图像，请使用[optimize_image.py](/optimize_image.py) 脚本。 脚本用法在这里解释[explained here](/doc/running-optimize-image.md).。
* To find images (for FC layers) or crops (for conv layers) from a set of images (e.g. the ImageNet training or validation set) that cause highest activation, use the [find_max_acts.py](/find_maxes/find_max_acts.py) script to go through the set of images and note the top K images/crops and then [crop_max_patches.py](/find_maxes/crop_max_patches.py) to use the noted max images / max locations to output the crops and/or deconv of the crops.

Results of both of the above steps will be saved as per-unit jpg image files, which can be loaded by the toolbox when browsing units. To do so, just point the `caffevis_unit_jpg_dir` setting to the directory containing the per-unit images.
