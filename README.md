# Pose-Neural-Fabric-Search

We integrate NAS with the task of human pose estimation. To make full use of the structure of human body and NAS' ability of learning structures of networks, we model body pose into multiple parts,each of which is predicted by a cell-based neural fabric.

# Steps

## Create the `o` directory to reserve each experiment's output
```
mkdir o  
```
## Train the model
```
python train.py \
--cfg configs/our3.yaml \
--exp_name o/your_train_experiment_name \
--gpu 0,1 
```
or
```
sh train_coco.sh
```
other training optional commands

```
--batchsize // change the default batchsize
--param_flop // report the parameters and FLOPs
--search search_method_name // options: ['None','random','sync','first_order_gradient','second_order_gradient']
--debug // debug the input data and visualization
--show_arch_value // print the parameters of architecture in the training process
```
## Test the model
```
python test.py --cfg configs/ours3.yaml --exp_name o/your_test_experiment_name --gpu 0,1 --test_model o/path_to_your_saved_model --flip_test 
```
other testing optional commands
```
--param_flop
---margin 1.15 // margin between bbox border and input size [1.0,1.5]
--flip_test // horizontal flip test
--use_dt // use the detection results of COCO val set or test-dev set
```

## Other settings of model.

All detailed setting of the model is recored in the `configs/*.yaml`.

# Exploration

About the `vector in pixel` method, we provide two convolutional mode `Conv2d` and `Conv3d` to implement the idea of how to construct the vector representation (`5D-Tensor`) of keypoint. We use the `Conv2d` mode (reshape `5D-Tensor` to `4D-Tensor`) to get the data in paper. The way of construting the vector represntation can be modified in more possible tricks，but the method of computing the 2-norm of each vector is determined.

# Experiments

coming soon.




 
