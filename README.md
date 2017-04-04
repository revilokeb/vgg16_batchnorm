# vgg16_batchnorm in Caffe
Caffe weights of VGG16 architecture with BatchNorm 

Here I have trained the VGG16 architecture with interleaved batch-norm layers on the ILSVRC12 dataset in Caffe. I have started the training  with all available weights initialized from the original VGG16 contribution (http://www.robots.ox.ac.uk/%7Evgg/research/very_deep/). I am using subtraction of channel mean as in the original publication and also keep biases (although they are not necessary).

The training dataset is the full ILSVRC12 training data resized to shorter side 256px. During training I do mirroring and random cropping (224 x 224) but no other data augmentation, see also train_val_vgg16bn.prototxt.

After 28 epochs the single center crop (224 x 224) validation accuracy is as follows (```caffe test -model train_val_vgg16bn.prototxt -weights vgg16bn_2_iter_1120000.caffemodel -gpu 0 -iterations 6250```):
* Top 1: 70.44% 
* Top 5: 89.94% 

This compares with the following single center crop (224 x 224) validation accuracy of the orginal weights from http://www.robots.ox.ac.uk/%7Evgg/research/very_deep/:
* Top 1: 70.38%
* Top 5: 89.38%

Link to the weights: https://drive.google.com/drive/folders/0B1qLpHDbczM2NGJwMHFDLTdNZkU?usp=sharing
