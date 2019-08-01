# Box_Discretization_Network
This repository is built on the **pytorch [[maskrcnn_benchmark]](https://github.com/facebookresearch/maskrcnn-benchmark)**. 

# Description
**Paper [[link]](https://arxiv.org/abs/1906.02371)**. 

This method is served as the foundation for our recent ICDAR 2019 ReCTs competition method [[link]](https://rrc.cvc.uab.es/?ch=12), which won the first place of the detection task.


# Getting Started

A basic guide for train and test. 

## Install anaconda 

Link：https://pan.baidu.com/s/1TGy6O3LBHGQFzC20yJo8tg psw：vggx

## Step-by-step install
 ```shell
conda create --name mb
conda activate mb
conda install ipython
pip install ninja yacs cython matplotlib tqdm scipy shapely
conda install pytorch=1.0 torchvision=0.2 cudatoolkit=9.0 -c pytorch
conda install -c menpo opencv
export INSTALL_DIR=$PWD
cd $INSTALL_DIR
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
python setup.py build_ext install
cd $INSTALL_DIR
git clone https://github.com/Yuliang-Liu/Box_Discretization_Network.git
cd Box_Discretization_Network
python setup.py build develop
```

## Pretrained model：

[[Link]](https://drive.google.com/file/d/1pBQ53ZNvsdu8byFKDST-de30X5pEFI7C/view?usp=sharing)
unzip under project_root

## ic15 data

Prepare data follow COCO format.
[[Link]](https://drive.google.com/file/d/16rpK9Ql4mZydl1CGPMQXf0Q8YQqtXnX7/view?usp=sharing)
unzip under datasets/

## Train

After downloading data and pretrained model, run
  ```shell
  bash quick_train_guide.sh
 ```

## Test with [[TIoU]](https://github.com/Yuliang-Liu/TIoU-metric)

Run 
 ```shell
 bash my_test.sh
```

Put kes.json to ic15_TIoU_metric/
inside ic15_TIoU_metric/

Run (conda deactivate; pip install Polygon2)
 ```shell
 python2 to_eval.py
```

Example results: 
* mask branch 79.4 (test segm.json by changing to_eval.py (line 10: mode=0) ); 
* kes branch 80.4; 
* in .yaml, set RESCORING=True -> 80.8;
* Set RESCORING=True and RESCORING_GAMA=0.8 -> 81.0;
* The mini example offers a pure baseline that takes less than 4 hours to finalize training with only official training data. One can try many other tricks such as **CROP_PROB_TRAIN**, **ROTATE_PROB_TRAIN**, **USE_DEFORMABLE**, **DEFORMABLE_PSROIPOOLING**, **PNMS**, **MSR**, **PAN** in the project, whcih were all tested effective to improve the results. To achieve state-of-the-art performance, extra data (syntext, MLT, etc.) and proper training strategies are necessary. 

## Visualization 

Run 
 ```shell
 bash single_image_demo.sh
```

# Citation
If you find our metric useful for your reserach, please cite
```
@article{liu2019omnidirectional,
  title={Omnidirectional Scene Text Detection with Sequential-free Box Discretization},
  author={Liu, Yuliang and Zhang, Sheng and Jin, Lianwen and Xie, Lele and Wu, Yaqiang and Wang, Zhepeng},
  journal={IJCAI},
  year={2019}
}
```

## Feedback 
Suggestions and discussions are greatly welcome. Please contact the authors by sending email to 
  `liu.yuliang@mail.scut.edu.cn` or `yuliang.liu@adelaide.edu.au`. For non-commercial usage, please contact Prof. Lianwen Jin via lianwen.jin@gmail.com.
